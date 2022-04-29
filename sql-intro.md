# SQL: Structured Query Language
Un linguaggio formale per gestire, dalla A alla Z, i database relazionali, compresi i **geo**database relazionali (GIS).

## Standard e dialetti

Lo **SQL** è atandard del American National Standards Institute (ANSI) dal 1986, e del International Organization for Standardization (ISO) dal 1987.

Nonostante ciò, molto raramente viene implementato nella sua forma standatizzata dai singoli produttori di RDBMS (Relational Database Management System), i quali introduccono spesso varianti dialettali, sia al fine di aggiungere nuove funzioni non previste nello standard, sia per semplificare il lavoro degli utenti, sia infine per rendere più difficile il passaggio dei dati daun sistema all'altro.
Tra i moltissimi prodotti disponibili, solo [PostgreSQL](https://www.postgresql.org/) implementa in maniera rigida lo standard.

### Esempi di dialetti, differenza di sintassi
La sintassi di **MySQL/MariaDB**, usa i _backtick_ (`` ` ``) per definire i nomi delle tabelle e dei campi

```sql
SELECT * FROM `siti` WHERE 1;
```

In **SQLite** possono essere usati indiferentemente  i _backtick_ (`` ` ``), i doppi apici (`"`),  i singoli apici (`'`) oppure nessuno di questi per defnire i nomi delle tabelle edei campi. Le seguenti espressioni sono tutte equivalenti:

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

- **DDL** (Data Definition Language) usato per  creare e modificare schemi di database, es.:
```SQL
CREATE TABLE "siti" (
	"id" INT PRIMARY KEY NOT NULL,
	"nome" CHAR(50) NOT NULL,
	"tipologia" CHAR(100) NOT NULL,
	"crono_da" INT,
	"crono_a" INT
);
```
- **DML** (Data Manipulation Language) usato per inserire, modificare e gestire dati memorizzati, es.:
```SQL
INSERT INTO "siti"
	("nome", "tipologia", "crono_da", "crono_a")
	VALUES
	('Roma', 'città', -753, 476);
```
- **DQL** (Data Query Language) usato per interrogare i dati memorizzati, es.:
```sql
SELECT *  FROM "siti" WHERE "tipologia" = 'città';
```
- **DCL** (Data Control Language) creare e gestire strumenti di controllo e accesso ai dati, es.:
```sql
CREATE USER jbogdani WITH ENCRYPTED PASSWORD 'my-very-secret-password'; 
```
