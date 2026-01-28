---
tags:
  - sql
---
# Interrogazioni SQL in QGIS

Il linguaggio SQL è usato in QGIS per analizzare i dati e per creare vari tematismi. In particolare viene usato per creare `filtri` e per la gestione avanzata della [Simbologia](Simbologia.md).

[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset: `sql`

Contenuto del dataset:
```
- esercizio-sql.qgz
- vettori.gpkg
```

1. Aprire il progetto `esercizio-sql.qgz`, oppure
2. Aprire un nuovo progetto QGIS
	1. Aggiungere Bing Satellite (`Web > QuickMapServices > Bing > Bing Satellite`)
	2. Aggiungere il vettore places contenuto in `vettori.gpkg`
3. Creare e testare i  filtri
	1. Introduzione al `Costruttore di interrogazioni`

## Esercizi
### Esercizio 1

Mostra tutti i siti che sono stati capitale di _nomós_

### Esercizio 2

Mostra tutti i siti che sono stati capitale di _nomós_ **e** la cui tipologia è `settlement`
Esemplificare tre metodi diversi, che per il dataset in oggetto restituiscono lo stesso risultato (`LIKE`, `OR`, `IN`)

### Esercizio 3

Mostra tutti i `settlement` e `settlement-modern` che sono stati capitale di _nomos_ 


### Esercizio 4

Mostra tutti i siti attivi  nel V sec. d.C.

