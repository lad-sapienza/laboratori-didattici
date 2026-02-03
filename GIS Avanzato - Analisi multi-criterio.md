---
tags:
  - adv
---
# GIS modulo avanzato: introduzione
In questo modulo avanzato verrà preso in considerazione un caso di studio concreto, una domanda di tipo archeologico relativa ad un ambito cronologico e geografico ben preciso.

La domanda archeologica potrebbe essere così formulata:
> Quali sono le aree dell'attuale regione del Lazio che presentano caratteristiche ottimali per lo sviluppo degli insediamenti di età romana imperiale, ma che ad oggi non hanno dato tracce sicure in tal senso?

Per rispondere in maniera concreta, per reperire i dati necessari a questo tipo di analisi e anche per capire concretamente quali analisi dovranno essere effettuate, è necessario esplicitare meglio la richiesta.
## I dati
### Limite geografico
Il limite geografico è l'informazione più semplice da capire e anche il dato più semplice da reperire. La **Regione del Lazio** ha dei confini amministrativi ben definiti che è semplice reperire online in formato GIS, in particolare i dati sono stati scaricati da: [https://www.diva-gis.org/gdata](https://www.diva-gis.org/gdata)
### Caratteristiche ottimali per l'insediamento: requisiti, dati, parametri
Questo è un elemento molto più difficile da definire e valutare e certamente molto più soggettivo.

Ai fini di questo esercizio, solo alcuni elementi verranno presi in esame, con parametri decisi a tavolino, ma che possono essere oggetto di discussione. Nello specifico, si ritengono particolarmente interessanti i seguenti elementi
1. vicinanza alla rete viaria
2. non immediata vicinanze alla rete idrica, che da sempre è causa di rischio, ma neppure troppo distante, visto che l'acqua è una risorsa costosa da trasportare
3. non eccessiva vicinanza a insediamenti esistenti, che “esauriscono” il potenziale dell'area
Per calcolare queste variabili abbiamo dunque bisogno di:
1. **una rete stradale di età romana imperiale**: elaborata dal [Ancient World Mapping Center](http://awmc.unc.edu/wordpress/) e liberamente disponibile in formato GIS, all'indirizzo http://awmc.unc.edu/awmc/map_data/shapefiles/ba_roads/
2. **Le estensioni interne di acqua (laghi)** sono disponibili sempre a cura del [Ancient World Mapping Center](http://awmc.unc.edu/wordpress/), in formato GIS, all'indirizzo: http://awmc.unc.edu/awmc/map_data/shapefiles/physical_data/inlandwater/
3. **La rete fluviale** è stata scaricata da https://www.diva-gis.org/gdata. Questo dato non è riferito specificatamente all'età romana, quindi al fine di rendere più corretta questa analisi sarebbe necessario un ulteriore lavoro su questo dato.
5. **La rete di insediamenti noti di età romana imperiale** è stata invece scaricata da [Pleiades](https://pleiades.stoa.org/), all'indirizzo: [http://atlantides.org/downloads/pleiades/kml/pleiades-latest.kmz](http://atlantides.org/downloads/pleiades/kml/pleiades-latest.kmz)
6. Infine, il modello digitale del terreno (DEM) con risoluzione di 30m è stato scaricato da [https://opentopography.org/](https://opentopography.org/), attraverso il plugin di `QGIS OpenTopography DEM Downloader`

[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset `adv`

Il prossimo passaggio riguarda la [Preparazione dei dati](Preparazione%20dei%20dati.md)