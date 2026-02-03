---
tags:
  - adv
---
# GIS: modulo avanzato: Analisi a criteri multipli

> Guida non archeologica disponibile a  
> [http://www.qgistutorials.com/it/docs/3/multi_criteria_overlay.html](http://www.qgistutorials.com/it/docs/3/multi_criteria_overlay.html)


1. Aprire il progetto QGIS, come si è venuto a creare dal [passaggio precedente](Calcolatore%20dei%20campi.md)
2. Raggruppare i livelli vettoriali (`fiumi-lazio`, `strade-lazio`, `acque-interne-lazio` e `insediamenti-imperiali`) in un gruppo chiamato `Step-1`
3. Rasterizzare i vettori del gruppo `Step-1`
	1. Menu `Processing` > `Strumenti`
    2. Nel panello che siapre cercare e aprire lo strumento `Rasterize (da vettore a raster)`
	    1. In `Parametri` selezionare `strade-lazio` come `Layer in ingresso`
    	3. Impostare come `valore fissato da scrivere` a `1,000000`
	    3. Impostare `unità di misura del raster in uscita` come `unità georeferenziate`
    	4. Impostare `larghezza/risoluzione orizzontale` a `15,000000`
	    5. Impostare `altezza/risoluzione verticale` a `15,000000`
	    6. Impostare `estensione risultato [opzionale]` come `confine-lazio`
	    7. In `attribuisci un determinato valore nullo alle bande in uscita` impostare `non impostato` cancellando il contenuto della casella che di default (è `0,000000`)
    	8. In `rasterizzato` salvare il nuovo file come `strade-raster`
    	![Pasted image 20220509153644](img/rasterizza-strade-1.png)
		![Pasted image 20220509153653](img/rasterizza-strade-2.png)
    3. Ripetere l'operazione sopra per gli altri layer: `fiumi-lazio`,  `acque-interne-lazio` e `insediamenti-imperiali` , utilizzando gli stessi parametri. Per quest'ultimo cambiare la risoluzione a 30x30m.
    4. Creare un gruppo di layer chiamato `Step-2` e includervi tutti i raster creati in questo passaggio
4. Creare un unico raster per l'idrografia
    1. Cercare e aprire nel panello processing `Calcolatore raster` (sotto `GDAL` > `Raster miscellanea`)
    2. Inserire l'espressione: `"acque-interne-raster@1" + "fiumi-raster@1"`
    3. Utilizzare `confine-raster` come `layer di riferimento`
    4. Salvare il file come `idrografia-3-valori`
    ![Pasted image 20220509155655](img/unione-fiumi-acque-interne.png)
	Il raster in uscita e cioè `raster_idrografia` avrà valore 1 nei pixel dove è presente un corso d'acqua.  
	**Importante**: le aree in cui si trovano sia corsi d'acqua (fiumi) che laghi avranno invece valore 2. Per correggere questo errore e riportare tutte le aree con laghi e fiumi al valore 1 seguire il prossimo step:
5. Eliminare valore 2 e sostituirlo con 1 nel layer `idrografia-3-valori`
    1. Aprire nuovamente il `Calcolatore raster`
    2. Utilizzare la seguente espressione: `"idrografia-3-valori@1" > 0`
    3. Salvare il file come `idrografia-raster`
6. Creare un gruppo di layer chiamato `Step-3` e includervi tutti i raster creati in questo passaggio
7. Analisi di prossimità (distanza raster)
    1. Aprire lo strumento `Prossimità (distanza raster)` (sotto `GDAL` > `Analisi raster`)
    2. In `layer di ingresso` selezionare `strade-raster`
    3. Come `unità di distanza` impostare `unità georeferenziate`
    4. Impostare come `massima distanza che deve essere generata` il valore `6000` (= 6km)
    5. Impostare `valore Nodata` a `non impostato`
    6. Salvare il file come `strade-prossimita`
    ![Pasted image 20220509161130](img/prossimita-idrografia.png)
    7. Aprire il pannello dello `stile dei layer`
    8. In `gradiente colore` impostare come valore massimo (max) `6000`
    9. Ripetere le stesse operazioni per i layer `idrografia-raster` e `insediamenti-raster`
8. Ricalssificazione strade, definendo tre classi, rispettivamente:
	 -  **100** che raccoglie le aree fino a 1km di distanza, 
	 -  **50** che raccoglie le aree tra 1km e 5 km e 
	 -  **10** che raccoglie le aree distanti più di 6km.
    1. Aprire il `calcolatore dei raster`
    2. Inserire la seguente espressione:  
	`100*("strade-prossimita@1"<=1000) + 50*("strade-prossimita@1">1000)*("strade-prossimita@1"<=6000) + 10*("strade-prossimita@1">6000)`
	3. In `Referencelayer(s)` selezionare `confine-lazio`
	4. Salvare il file come `strade-riclassificato`
	![](img/strade-classificate.png)
9. Riclassificazione acque, definendo tre classi, rispettivamente:
	 -  **100** che raccoglie le aree oltre i 6km di distanza, 
	 -  **50** che raccoglie le aree tra 1km e 6 km e 
	 -  **10** che raccoglie le aree distanti meno di 1km.
    1. Aprire il `calcolatore dei raster`
    2. Inserire la seguente espressione:  
	`100*("idrografia-prossimita@1">6000) + 50*("idrografia-prossimita@1">1000) * ("idrografia-prossimita@1"<=6000) + 10*("idrografia-prossimita@1"<1000)`
	3. In `Referencelayer(s)` selezionare `confine-lazio`
	4. Salvare il file come `idrografia-riclassificato`
10. Riclassificare gli insediamenti, definendo tre classi, rispettivamente:
	 -  **100** che raccoglie le aree oltre i 6km di distanza, 
	 -  **50** che raccoglie le aree tra 1km e 6 km e 
	 -  **10** che raccoglie le aree distanti meno di 1km.
    1. Aprire il `calcolatore dei raster`
    2. Inserire la seguente espressione:  
	`100*("insediamenti-prossimita@1">6000) + 50*("insediamenti-prossimita@1">1000) * ("insediamenti-prossimita@1"<=6000) + 10*("insediamenti-prossimita@1"<1000)`
	3. In `Referencelayer(s)` selezionare `confine-lazio`
	4. Salvare il file come `insediamenti-riclassificato`
	![](img/Pasted%20image%2020220510153347.png)
11. Analisi finale
    1. Aprire il `calcolatore dei raster`
    2. Inserire la seguente espressione:  
    `("strade-riclassificate@1" + "idrografia-riclassificata@1")*("insediamenti-riclassificati@1" != 1 ) * "confine-raster@1"`
	3. In `Referencelayer(s)` selezionare `confine-lazio`
	4. 4. salvare il file come `overlay`
1. Impostare simbologia `banda singola falso colore`
	- Aprire le proprietà del layer
    - In tipo di visualizzazione impostare `banda singola falso colore`
    - Classificare

[< Calcolatore dei campi](Calcolatore%20dei%20campi.md)