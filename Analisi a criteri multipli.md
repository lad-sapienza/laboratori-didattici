---
tags:
  - adv
---
# Analisi a criteri multipli

1. Rasterizzare dati vettoriali
	1. Rasterizzare il layer dei **confini**
	2. Rasterizzare il layer dei **fiumi**
	2. Rasterizzare il layer dei **inseldiamenti**
	3. Rasterizzare il layer dei **laghi**
	4. Rasterizzare il layer dei **strade**
2. Unire **laghi** e **fiumi** in un raster chiamato **idrografia**
3. Analisi di prossimità
	1. Analisi di prossimità per **idrografia**
	2. Analisi di prossimità per **strade**
	3. Analisi di prossimità per **insediamenti**
4. Riclassificare le analisi di prossimità
	1. Riclassificare **idrografia**
	2. Riclassificare **strade**
	3. Riclassificare **insediamenti**
5. Creare il raster si analisi.

[[Calcolatore dei campi| < Passaggio precedente]]

## Guida modulo GIS Avanzato - Multi criteria analysis (raster)

1. caricare su QGIS `lazio_dati`

2. Rasterizzare i vettori presenti in `lazio_dati`

    - Aprire lo strumento `Rasterize (da vettore a raster)`
    - In `Parametri` selezionare `strade` come `Layer in ingresso`
    - impostare come `valore fissato da scrivere` a `1,000000`
    - impostare `unità di misura del raster in uscita` come `unità georeferenziate`
    - impostare `larghezza/risoluzione orizzontale` a `15,000000`
    - impostare `altezza/risoluzione verticale` a `15,000000`
    - impostare `estensione risultato [opzionale]` come `confini_lazio_moderni`
    - in `attribuisci un determinato valore nullo alle bande in uscita` impostare `non impostato` cancellando il contenuto della casella che di default è `0,000000`
    - in `rasterizzato` salvare il nuovo file come `raster_strade`

    - ripetere l'operazione sopra per i layer `laghi`; `insediamenti`; `fiumi`; `confini_moderni_lazio` utilizzando gli stessi parametri

3. Creare un unico raster per l'idrografia (merge raster)

    - Aprire il `Calcolatore di raster`
    - inserire l'espressione: "raster_fiumi@1" + "raster_laghi@1"
    - utilizzare `raster_laghi` come `layer di riferimento`
    - salvare il file come `raster_idrografia`

Il raster in uscita e cioè `raster_idrografia` avrà valore 1 nei pixel dove è presente un corso d'acqua.
IMPORTANTE: le aree in cui si trovano sia corsi d'acqua (fiumi) che laghi avranno invece valore 2. Per correggere questo errore e riportare tutte le aree con laghi e fiumi al valore 1 seguire il prossimo step:

4. Eliminare valore 2 e sostituirlo con 1 nel layer `raster_idrografia`

    - Aprire nuovamente il `calcolatore raster`
    - utilizzare la seguente espressione: "raster_idrografia@1" > 0
    - salvare il file come `raster_idrografia_unita`

5. Prossimità (distanza raster)

    - aprire lo strumento `prossimità (distanza raster)`
    - in `layer di ingresso` selezionare `raster_strade`
    - come `unità di distanza` impostare `unità georeferenziate`
    - impostare come `massima distanza che deve essere generata` il valore `5000`
    - impostare `valore Nodata` a `non impostato`
    - salvare il file come `raster_proximity_road`

    - aprire il pannello dello `stile dei layer`
    - in `gradiente colore` impostare come valore massimo (max) `5000`

    - ripetere la stessa operazione per i layer `raster_idrografia_unita` e `raster_insediamenti`

6. Ricalssificazione strade

    - aprire il `calcolatore dei raster`
    - inserire la seguente espressione: 

    100*(“raster_proximity_road@1"<=1000) + 50*("rraster_proximity_road@1">1000)*("raster_proximity_road@1"<=5000) + 10*("raster_proximity_road@1">5000)

    - salvare il file come `strade_riclassificato`

7. Riclassificazione acque

    - aprire il `calcolatore dei raster`
    - inserire la seguente espressione: 

    100*("raster_proximity_acque@1">5000) + 50*("raster_proximity_acque@1">1000) * ("raster_proximity_acque@1"<=5000) + 10*("raster_proximity_acque@1"<1000)

    - salvare il file come `acque_riclassificato`

8. Riclassificare gli insediamenti

    - aprire il `calcolatore dei raster`
    - inserire la seguente espressione: 

    100*("raster_proximity_insediamenti@1">5000) + 50*("raster_proximity_insediamenti@1">1000) * ("raster_proximity_insediamenti@1"<=5000) + 10*("raster_proximity_insediamenti@1"<1000)

    - salvare il file come `acque_riclassificato`

9. Analisi finale

    - aprire il `calcolatore dei raster`
    - inserire la seguente espressione:

    ("strade_riclassificato@1" + "acque_riclassificato@1")*("raster_insediamenti@1"  !=  1 ) * "raster_confini@1"

    - salvare il file come `overlay`

10. Impostare simbologia `banda singola falso colore`

    - aprire le proprietà del layer
    - in tipo di visualizzazione impostare `banda singola falso colore`
    - classificare
