---
tags:
  - georef
  - raster
---
# Georiferire dati raster con coordinate
[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset: `georef-coord`

Contenuto:
```
- cairo-city-maps-1958/
	- txu-oclc-47175049-cairo1-1958.jpg
	- txu-oclc-47175049-cairo2-1958.jpg
	- txu-oclc-47175049-cairo3-1958.jpg
- ministry-of-finance/
	- 10285081.jp2
	- 10285082.jp2
```

## Dataset  di esempio #1: Cairo City Map 1958

### Metadati generali
- Sistema di Riferimento: **ED50 / UTM zone 36N (EPSG:23036)**
- Coordinate rosse: Egypt Red Belt (EPSG:22992)
- Coordinate geografiche in ED50 (EPSG: 4230)
- Pagina iniziale d’indirizzo: https://legacy.lib.utexas.edu/maps/egypt.html

> Info:
> [epsg.io] (https://epsg.io)
> 

### Metadati singole carte fornite:
- Cairo No. 1,
    1:10,000
    Edition 4-AMS, Series P971. U.S. Army Map Service, 1958
    6.9MB
    txu-oclc-47175049-cairo1-1958
    http://legacy.lib.utexas.edu/maps/world_cities/txu-oclc-47175049-cairo1-1958.jpg

- Cairo No. 2
    1:10,000
    Edition 4-AMS, Series P971. U.S. Army Map Service, 1958
    5.8MB
    txu-oclc-47175049-cairo2-1958
    http://legacy.lib.utexas.edu/maps/world_cities/txu-oclc-47175049-cairo2-1958.jpg

- Cairo No. 3
    1:10,000
    Edition 4-AMS, Series P971. U.S. Army Map Service, 1958
    8MB
    txu-oclc-47175049-cairo3-1958
    http://legacy.lib.utexas.edu/maps/world_cities/txu-oclc-47175049-cairo3-1958.jpg


## Dataset  di esempio #2: Ministry of finance

### Metadati generali
- Sistema di Riferimento: **Egypt 1907  (EPSG:4229)**
- Info: https://epsg.io/4229
- Fonte: David Rumsey Historical Map Collection

## Diversi modi di definire le coordinate geografiche
- **DD MM SS.SS**: Gradi Minuti Secondi.decimali di secondi (Degrees Minutes Seconds) usa gli spazi per separare l'indicazione dei gradi, minuti e secondi, usando un sistema sessagesimale (base 60) di conteggio: 1°= 60'; 1'=60". Ulteriore precisione, sotto al secondo, è possibile definirla fornendo anche i decimali di secondo, usando un sistema decimale (base 10)
- **DD.DD**: Gradi.decimali di grado mantiene il grado come unità di misura, ma converte il sistema sessagesimale in un sistema decimale, convertendo minuti e secondi. La formula del calcolo è piuttosto semplice:
	`DD MM SS.ss` = `DD+(MM/60)+(SS.ss/360)`
	Es.:
		- **30° 30' 00"** = 30 + (30/60) + (0/3600) = **30,5°**
		- **30° 45' 30"** = 30 + (40/60) + (30/3600) = **30,675°**
 