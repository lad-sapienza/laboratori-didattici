---
tags:
  - vectors
  - symbology
---
# Simbologia
Nello sviluppo degli utilimi anni di QGIS, la simbologia ha assunto un valore sempre più importante e ha sostituito nella maggiorparte dei casi l'utilizzo dei filtri.

[[Accesso ai dati]] > Dataset: `symbology`

Contenuto dataset:
```
- esercizio-simbologia.qgz
- vettori.gpkg
```

1. Aprire il progetto `esercizio-simbologia.qgz`, oppure
2. Aprire un nuovo progetto QGIS
	1. Aggiungere Bing Satellite (`Web > QuickMapServices > Bing > Bing Satellite`)
	2. Aggiungere `places` contenuto in `vettori.gpkg`

## Esercizio 1: modificare la simbologia di fiumi e ponti
...

## Esercizio 2: simbologia avanzata
Modificare la simbologia del layer `vettori - places` come segue:
- `rosso`: Capitali di nomos poi diventati sedi episcopali
- `verde`: Capitali di nomos NON diventati sedi episcopali
- `blu`: Sedi episcopali che non erano prima capitrali di nomos
I luoghi che non corrispondono a nessuno di questi requisiti non dovranno essere visualizzati