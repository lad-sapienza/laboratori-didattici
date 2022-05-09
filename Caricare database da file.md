---
tags:
  - other-formats
---
## Caricare database da file
[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset: `other-formats`

File da usare:
- `site_attr.csv`
- `site_attr.xlsx`
Esempio di contenuto (prime 10 righe):
```csv
id,name,pleiades,typology,episcopalsee,isnomoscapital,datefrom,dateto
1,Memphis,736963,,1,,,
2,Letopolis,727149,settlement,1,1,325,750
3,Sais,727217,settlement,1,1,326,1100
4,Xois,727256,settlement,1,1,,
5,Hermopolis Mikra,727123,settlement-modern,1,1,325,1300
6,Heroonpolis,727124,,,1,,
7,Bousiris,727090,settlement,1,1,301,1100
8,Athribis,727078,settlement,1,1,301,1000
9,Leontopolis (Tell el-Moqdam),727147,settlement,1,1,301,900
```
1. Su QGIS: `CTRL+L` (o `CMD+L` su MacOS)
2. Click a sinistra su `Testo delimitato`
3. `Nome file`: naviga e seleziona `site_attr`
4. **Formato file**: `CSV`
5. **Opzioni Record e Campi**: `Il primo record ha il nome dei campi`
6. **Definizione della geometria**: Nessuna geometria (solo tabella attributi)
7. Click su `Aggiungi`
8. Click su `Close`
---
Allo stesso risultato si può arrivare anche trascinando semplicemente il file `site_attr.csv` nel pannello dei layer.
Nello stesso modo si possono caricare anche altri formati, come per esempio MS Excel: `site_attr.xlsx`
