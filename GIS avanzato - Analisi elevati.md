---
tags:
  - adv
  - prospetti
---
# Introduzione
Questo modulo è finalizzato all'utilizzo _non geografico_ di QGIS per l'analisi statistica ed automatizzata delle tessiture murarie.
Come dato di partenza verrà utilizzato un file AutoCAD con il rilievo di dettaglio di un prospetto murario, per comodità, con grandi superfici in laterizio, che verrà trasformato per rendere possibili analisi quantitative.
Per questo motivo verrà usato il prospetto PNE_usm 47-b degli scavi del Palatino (dir. prof.ssa M.Teresa D'Alessio).

## Pre-processamento dei dati
### DWG -> DXF
Per l'uso di file CAD in QGIS è necessario salvare il file in formato AutoCAD DWG in formato [AutoCAD DXF](https://en.wikipedia.org/wiki/AutoCAD_DXF) utilizzando un programma CAD capace di leggere i file DWG. 
> **QGIS, per motivi di licenza, non gestisce i file proprietari DWG**.

Come risultato si ha il file di output `PNE_usm 47-b.dxf`
**Attenzione**: si tratta di una semplificazione del prospetto originario.
### Convertire le polilinee in poligoni
- Caricare il DXF in QGIS e convertire le linee in poligoni, ottenendo come output un layer temporaneo: `Vettore` > `Strumenti di geometria` > `Da linee a poligoni`  
  > Se fallisce, andare su impostazioni e selezionare `Salta (Ignora) Elementi con Geometrie non valide`.
- Impostare la trasparenza a 50% per verificare “a occhio” il risultato.
- Eventualmente correggere manualmente gli errori
- Eseguire un controllo di validità delle geometrie: `Vettore` > `Strumenti di geometria` > `Controllo di validità...`
- Nuovamente, sistemare manualmente possibili errori, eventualmente eseguire `Ripara geometrie`
- Dividere il poligono di `limite` dagli altri.
---
Prossimo passo:
- [Analisi preliminare delle misure romane](Analisi%20preliminare%20delle%20misure%20romane.md)
