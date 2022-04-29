## Caricamento Tiles XYX

[[Accesso ai dati]] > Dataset: `other-formats`

Per questo esercizio useremo i dati della cartografia napoleonica d'Egitto, pubblicati a cura del [LAD](https://lad.saras.uniroma1.it) sul portale di documentazione di PAThs, all'indirizzo: https://docs.paths-erc.eu/data/

1. Navigare con il browser all'indirizzo: https://docs.paths-erc.eu/data/
2. Scorrere la pagina fino a **Composite: A Map of Lower Egypt from Various Surveys by A. Arrowsmith**, oppure usare la casella di ricerca
3. Click su `More`
4. Selezionare e copiare l'indirizzo che si trova sotto **Tiled web map**, ovvero: ``https://swift.cloud.garr.it/swift/v1/arrowsmith-1807/{z}/{x}/{y}.png``
5. Andare su QGIS e aggiungere un nuovo vettore:
`Layer` > `Aggiungi Layer` > `Aggiungi Layer XYZ...` 
oppure
`CTRL+L` (`CMD+L` su MacOS) > `XYZ`
6. Click su `Nuovo`
7. Inserire un nome significatico per la risorsa, es. `Delta egiziano di Arrowsmith`
8. Incollare in URL l'indirizzo copiato dal sito di PAThs: `https://swift.cloud.garr.it/swift/v1/arrowsmith-1807/{z}/{x}/{y}.png`
9. Click su `OK`
10. Selezionare la risorsa dal menu a tendine epoi click su `Aggiungi`
11. Click su `Close`