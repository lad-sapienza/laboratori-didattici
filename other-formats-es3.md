---
tags:
  - other-formats
---
## JOIN
[[Accesso ai dati]] > Dataset: `other-formats`

QGIS permette di arricchire un layer di geomatrie caricato in un progetto, con attributi provenienti da un database esterno, sempre caricati sul progetto.

Come in tutti i RDBMS per unire due tabelle è necessario che entrambe abbiano un campo che contiene gli stessi valori, che funga da mappa per mettere in relazione i record.

File da usare: `site_coord.csv`
Esempio di contenuto (prime 4 righe):
```csv
nord,est,id
29.849491,31.255061,1
30.1223455,31.1339825,2
30.96715,30.774367,3
31.0882220246915,30.9505891799927,4
```
File da usare:
- `site_attr.csv`
Esempio di contenuto (prime 10 righe):
```csv
id,name,pleiades,typology,episcopalsee,isnomoscapital,datefrom,dateto
1,Memphis,736963,,1,,,
2,Letopolis,727149,settlement,1,1,325,750
3,Sais,727217,settlement,1,1,326,1100
4,Xois,727256,settlement,1,1,,
```
Nel caso presente in entrambele tabelle il campo si chiama `id` e contiene l'identificativo univoco del sito. Senza questa indicazione sarebbe impossibile eseguire l'unione (`JOIN`). I campi possono essere (spesso lo sono) nominato con nomi diversi, ma è importante che siano della stessa tipologia (numerico, testuale, ecc) e contengano gli stessi dati.

1. Click destro su `site_coord` nel panello dei layer > Proprietà
2. Click su tab `Join`
3. Click su bottone `+`
	1. Vettore di Join: `site_attr`
	2. Campo unione: `id`
	3. Campo destinazione: `id`
	4. OK
4. OK
5. Click destro su `site_coord` nel panello dei layer > Apri Tabella Attributi
