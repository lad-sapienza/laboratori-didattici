# Sintassi SQL di base (DQL, interrogazione)

## 1. Struttura base
Ogni asserzione ha una struttura tripartita:   `nome campo` + `operatore` + `valore`

**Esempio**:
```SQL
"isnomoscapital" = '1'
```


## 2. Composizione delle asserzioni
È possibile comporre interrogazioni complesse unendo insieme più di una asserzione semplice con gli operatori `AND` o `OR`. `AND` è più esclusivo (più filtri = meno risultati), mentre or è più permissivo (meno filtri = più risultati).

**Esempio**:
```sql
"isnomoscapital" = '1' AND "episcopalsee" = '1'
```

```sql
"isnomoscapital" = '1' OR "episcopalsee" = '1'
```

### 3. Definizine delle priorità
È possibile usare le parentesi per definire delle priorità di valutazione delle varie operazioni, esattamente come succede in matematica, dove:
```
3 + 2 * 5 != (3+2) * 5
```

**Esempio**:
```sql
"isnomoscapital" = '1' 
AND 
"typology" = 'settlement' 
OR 
"typology" = 'settlement-modern'
```

restituisce 28 elementi, mentre: 
```sql
"isnomoscapital" = '1' 
AND 
(
 "typology" = 'settlement' 
 OR 
 "typology" = 'settlement-modern'
)
```
restituisce 27 elementi.

## Operatori SQL
### `=`
Trova esattamente il valore contenuto nella striga di riferimento:
```sql
"typology" = 'settlement'
```
troverà `settlement` ma non `settlement-modern`

### `LIKE`
Permette di usare il `wildcard`, ovvero carattere jolly `%` che sta per `ogni possibile carattere 0, 1o più volte`, es.:
```sql
"typology" LIKE 'settlement%'
```
troverà tutti quei record il cui campo `typology` inizia con il valore `settlement` e può proseguire (o no) con qualsiasi altro valore. Troverà `settlement`, ma anche `settlement-modern`, ma non troverà: `modern settlement`.
Per contro:
```sql
"typology" LIKE '%settlement'
```
troverà sia `settlement` che `modern settlement`, ma non `settlement-modern`.

Invece
```sql
"typology" LIKE '%settlement%'
```
troverà tutti i valori che contengono la stringa `settlement` in qualsiasi posizione.

Il carattere jolly può essere usato anche i posizione intermedia, per ovviare, per esempio, ai non frequenti anomalie di dati dovuti a errori o grafie alternative, es:

` "typology" LIKE 'set%lement'` troverà sia la forma corretta `settlement` che quella sbagliata `setlement`. Ugualmente `arch%eology` troverà le forme entrambe corrette di `archaeology` ed `archeology`.
### `<`,  `>`, `<=` e `>=`
Permettono di confrontare valori (principalmente) numerici, es:
```sql
"datefrom" > 200 AND "dateto" <= 1000
```

### `IN`
Permette do fornire una lista di valori per il confronto ed è sufficiente un solo riscontro positivo, es:
```sql
"typology" IN ("settlement", "settlement-modern")
```
È quindi equivalente (più sintetico) di una serie di `=/OR`:
```sql
"typology" = "settlement" OR  "typology" = "settlement-modern"
```

### `NOT IN`
È la negazione di `IN`.