---
tags:
  - other-formats
---
## Caricamento Tiles vettoriali
[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset: `other-formats`

Per questo esercizio useremo i dati della cartografia napoleonica d'Egitto, pubblicati a cura del [LAD](https://lad.saras.uniroma1.it) su GitHub, all'indirizzo: [https://github.com/lad-sapienza/jacotin-1828](https://github.com/lad-sapienza/jacotin-1828)

1. L'indirizzo dei Vector Web Tiles relativi a questo dataset è: `https://lad-sapienza.github.io/jacotin-1828/tiles/{z}/{x}/{y}.pbf`
2. Andare su QGIS e aggiungere un nuovo vettore:
`Layer` > `Aggiungi Layer` > `Aggiungi un Layer Tassello Vettoriale...` 
oppure
`CTRL+L` (`CMD+L` su MacOS) > `Tassello vettoriale`
6. Click su `Nuovo`
7. Inserire un nome significativo per la risorsa, es. `Jacotin 1828: LAD-GitHub`
8. Incollare in URL l'indirizzo di cui sopra: `https://lad-sapienza.github.io/jacotin-1828/tiles/{z}/{x}/{y}.pbf`
9. Click su `OK`
10. Selezionare la risorsa dal menu a tendine e poi click su `Aggiungi`
11. Click su `Close`

**A differenza dei tiles raster, la [Simbologia](Simbologia.md) di quelli vettoriali può essere modificata**