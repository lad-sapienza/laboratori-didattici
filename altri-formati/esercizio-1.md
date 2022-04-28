## Caricare geometrie da lista di coordinate
File da usare: `site_coord.csv`
Esempio di contenuto (prime 10 righe):
```csv
nord,est,id
29.849491,31.255061,1
30.1223455,31.1339825,2
30.96715,30.774367,3
31.0882220246915,30.9505891799927,4
31.033655,30.4707825,5
30.552892,32.099321,6
30.913368,31.2387955,7
30.4725912552293,31.1844185250811,8
30.683333,31.35,9
```
1. Su QGIS: `CTRL+L` (o `CMD+L` su MacOS)
2. Click a sinistra su `Testo delimitato`
3. `Nome file`: naviga e seleziona `site_coord`
4. **Formato file**: `CSV`
5. **Opzioni Record e Campi**: `Il primo record ha il nome dei campi`
6. **Definizione della geometria**: Coordinate punto: Campo X: est; Campo X: nord
7. Click su `Aggiungi`
8. Click su `Close`
