---
tags:
  - other-formats
---
## Caricamento GeoJSON remoto
[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset: `other-formats`

Per questo esercizio useremo i dati della cartografia napoleonica d'Egitto, pubblicati a cura del [LAD](https://lad.saras.uniroma1.it) su GitHub, all'indirizzo: https://github.com/lab-archeologia-digitale/jacotin-1828

1. Navigare con il browser all'indirizzo: https://github.com/lab-archeologia-digitale/jacotin-1828
2. Navigare fino alla cartella `data/hydrography/hydrography_plg.geojson`
3. Click su download
4. Selezionare e copiare l'URL (https://raw.githubusercontent.com/lab-archeologia-digitale/jacotin-1828/master/data/hydrography/hydrography_plg.geojson)
5. Andare su QGIS e aggiungere un nuovo vettore:
`Layer` > `Aggiungi Layer` > `Aggiungi Layer Vettore...`
6. Incollare nella casella `Sorgente / Dataset vettoriale` l'URL copiato
7. Click su `Aggiungi`
8. Click su `Close`
9. Ripetere i passaggi 2-8 anche per:
	1. `data/hydrography/hydrography_pll.geojson`
	2. `data/hydrography/bridges.geojson`
	3. `data/hydrography/coastline.geojson`

