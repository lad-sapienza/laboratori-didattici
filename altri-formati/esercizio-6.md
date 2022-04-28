## Caricamento Tiles vettoriali
Per questo esercizio useremo i dati della cartografia napoleonica d'Egitto, pubblicati a cura del [LAD](https://lad.saras.uniroma1.it) su GitHub, all'indirizzo: https://github.com/lab-archeologia-digitale/jacotin-1828

1. L'indirizzo dei Vector Web Tiles relativi a questo dataset è:
`https://lab-archeologia-digitale.github.io/jacotin-1828/tiles/{z}/{x}/{y}.pbf`
2. Andare su QGIS e aggiungere un nuovo vettore:
`Layer` > `Aggiungi Layer` > `Aggiungi un Layer Tassello Vettoriale...` 
oppure
`CTRL+L` (`CMD+L` su MacOS) > `Tassello vettoriale`
6. Click su `Nuovo`
7. Inserire un nome significatico per la risorsa, es. `Jacotin 1828: LAD-GitHub`
8. Incollare in URL l'indirizzo di cui sopra: `https://lab-archeologia-digitale.github.io/jacotin-1828/tiles/{z}/{x}/{y}.pbf`
9. Click su `OK`
10. Selezionare la risorsa dal menu a tendine e poi click su `Aggiungi`
11. Click su `Close`

**A differenza dei tiles raster, la simbologia di quelli vettoriali può essere modificata**