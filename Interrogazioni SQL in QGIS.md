---
tags:
  - sql
---
# Interrogazioni SQL in QGIS

Il linguaggio SQL è usato in QGIS per analizzare i dati e per creare vari tematismi. In particolare viene usato per creare `filtri` e per la gestione avanzata della [[Simbologia]].

[[Accesso ai dati]] > Dataset: `sql`

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

## Sintassi di base SQL.
[[Sintassi SQL (DQL) di base|Sintassi SQL di base, per interrogazioni]]


## Filtro 1: tutti i siti che sono stati capitale di _nomós_
```sql
"isnomoscapital" = '1'
```

## Filtro 2: tutti i siti che sono stati capitale di _nomós_ e la cui tipologia è `settlement`
```sql
"typology" = 'settlement'

AND

"isnomoscapital" = '1'
```

## Filtro 3: tutti i `settlement` e `settlement-modern` che sono stati capitale di _nomos_ 
```sql
# TODO
```

# Filtro 4: siti attivi  nel V sec. d.C.
```sql
"datefrom" < 500 AND "dateto" > 500
```


## Riassunto: tre query diverse che danno lo stesso risultato:
```sql
"isnomoscapital" = '1'
 AND 
 "typology" LIKE 'setlement%'
```

e

```sql
"isnomoscapital" = '1'
 AND 
 "typology" IN ('setlement', 'setlement-modern')
```

e

```sql
"isnomoscapital" = '1'
 AND 
 (
	 "typology"  = 'setlement'
	 OR
	 "typology"  = 'setlement-modern'
 )
```

