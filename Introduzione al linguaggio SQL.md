---
tags:
  - sql
---
# SQL: Structured Query Language
Un linguaggio formale per gestire, dalla A alla Z, i database relazionali, compresi i **geo**database relazionali (GIS).

## Standard e dialetti

Lo **SQL** è standard del American National Standards Institute (ANSI) dal 1986, e del International Organization for Standardization (ISO) dal 1987.

Nonostante ciò, molto raramente viene implementato nella sua forma standartizzata dai singoli produttori di RDBMS (Relational Database Management System), i quali introducono spesso varianti dialettali, sia al fine di aggiungere nuove funzioni non previste nello standard, sia per semplificare il lavoro degli utenti, sia infine per rendere più difficile il passaggio dei dati da un sistema all'altro.
Tra i moltissimi prodotti disponibili, solo [PostgreSQL](https://www.postgresql.org/) implementa in maniera rigida lo standard.

### Esempi di dialetti, differenza di sintassi
La sintassi di **MySQL/MariaDB**, usa i _backtick_ (`` ` ``) per definire i nomi delle tabelle e dei campi

```sql
SELECT * FROM `siti` WHERE 1;
```

In **SQLite** possono essere usati indifferentemente  i _backtick_ (`` ` ``), i doppi apici (`"`),  i singoli apici (`'`) oppure nessuno di questi per definire i nomi delle tabelle e dei campi. Le seguenti espressioni sono tutte equivalenti:

```sql
SELECT * FROM `siti` WHERE 1;
SELECT * FROM "siti" WHERE 1;
SELECT * FROM 'siti' WHERE 1;
SELECT * FROM  siti  WHERE 1;
```

**PostgreSQL**, come anche **QGIS** ammette, seguendo lo standard, solo i doppi apici (`"`). La loro mancanza o ogni altro carattere risulterà in un errore di sintassi. I singoli apici sono riservati per indicare esclusivamente le stringhe di testo.

```sql
SELECT * FROM "siti" WHERE 1=1;
```

## Sotto-linguaggi
Lo SQL presenta uno strumentario molto ricco per interagire con i database. A seconda dell'utilizzo, possono essere definiti **informalente** dei sotto-liguaggi, tutti insieme :

**DDL** (Data Definition Language) usato per  creare e modificare schemi di database, es.:
```sql
CREATE TABLE "siti" (
	"id" INT PRIMARY KEY NOT NULL,
	"nome" CHAR(50) NOT NULL,
	"tipologia" CHAR(100) NOT NULL,
	"crono_da" INT,
	"crono_a" INT
);
```

**DML** (Data Manipulation Language) usato per inserire, modificare e gestire dati memorizzati, es.:
```sql
INSERT INTO "siti"
	("nome", "tipologia", "crono_da", "crono_a")
	VALUES
	('Roma', 'città', -753, 476);
```

**DQL** (Data Query Language) usato per interrogare i dati memorizzati, es.:
```sql
SELECT *  
  FROM 
    "siti" 
  WHERE 
    "tipologia" = 'città';
```

**DCL** (Data Control Language) creare e gestire strumenti di controllo e accesso ai dati, es.:
```sql
CREATE USER jbogdani WITH ENCRYPTED PASSWORD 'my-very-secret-password'; 
```


---

## Sintassi SQL di base (DQL, interrogazione)

### Struttura base (regola d'oro)

Ogni asserzione ha una struttura tripartita:   

> `nome campo` `operatore` `valore`


**Esempio**:
```sql
"cognome" = 'Rossi'
```


### Composizione delle asserzioni
È possibile comporre interrogazioni complesse unendo insieme più di una asserzione semplice con gli operatori `AND` o `OR`. `AND` è più esclusivo (**più** restituiscono **meno** risultati), mentre `OR` è più permissivo (**più** filtri restituiscono **più** risultati).

**Esempio**:
```sql
"cognome" = 'Rossi'
AND
"nome" = 'Mario'
```

```sql
"cognome" = 'Rossi' 
OR 
"cognome" = 'Doe'
```

### Definizione delle priorità
È possibile usare le **parentesi** per definire delle priorità di valutazione delle varie operazioni, esattamente come succede in matematica, dove:

```
3 + 2 * 5 != (3+2) * 5
```

**Esempio**
La query qui sotto è ambigua, se non conosciamo la priorità degli operatori:
```sql
"cognome" = 'Rossi' 
AND 
"nome" = 'Mario' 
OR 
"nome" = 'Giovanni'
```

Nel linguaggio SQL l'ordine di valutazione è:
1. `NOT`
2. `AND`
3. `OR`
Quindi la query sopra estrarrà dal database:

> **tutte le persone che si chiamano `Mario Rossi` ed anche tutte le persone che si chiamano `Giovanni` (con qualsiasi cognome)**

In questi termini è equivalente a:
```sql
(
  "cognome" = 'Rossi'
  AND
  "nome" = 'Mario'
)
OR
"nome" = 'Giovanni'
```

Se invece vogliamo tutti i componenti della famiglia Rossi che si chiamano Mario o Giovanni, dobbiamo scrivere:

```sql
"cognome" = 'Rossi' 
AND 
(
  "nome" = 'Mario' 
  OR 
  "cognome" = 'Giovanni'
)
```


## Operatori SQL
### Operatore `=`

Trova esattamente il valore contenuto nella striga di riferimento:

```sql
"nome" = 'Mario'
```

troverà tutti i `Mario`

### Operatore `LIKE`

Permette di usare il `wildcard`, ovvero carattere jolly `%` che sta per `ogni possibile carattere 0, 1 o più volte`, es.:
```sql
"nome" LIKE 'mari%'
```
troverà tutte le persone il cui nome comincia con `Mari...`. Troverà dunque:
- `Mario`
- `Maria`
- `Maria Francesca`
- `Mariangela`
- ecc...

Mentre:
```sql
"nome" LIKE '%mari%'
```

troverà tutti i valori che contengono la stringa `mari` in qualsiasi posizione, quindi anche:

- `Francesca Maria`
- `Giammaria`
- `Francescamaria`
- `Annamaria`

Il carattere jolly può essere usato anche i posizione intermedia, per ovviare, per esempio, ai non frequenti anomalie di dati dovuti a errori o grafie alternative, es:

```sql
"nome" LIKE 'gia%maria'
```

troverà:
- `Giammaria`
- `Gianmaria`
- `Giamaria`

### Operatori `<`,  `>`, `<=` e `>=`
Permettono di confrontare valori (principalmente) numerici, es:
```sql
"eta" > 18 AND "eta" <= 40
```

### Operatore `IN`
Permette do fornire una lista di valori per il confronto ed è sufficiente un solo riscontro positivo, es:

```sql
"anno_immatricolazione" IN (2023, 2024, 2025)
```

È quindi equivalente (più sintetico) di una serie di `OR`:

```sql
"anno_immatricolazione" = 2023
OR 
"anno_immatricolazione" = 2024
OR
"anno_immatricolazione" = 2025
```

### Operatore `NOT IN`

È la negazione di `IN`, es:

```sql
"anno_immatricolazione" NOT IN (2023, 2024, 2025)
```
