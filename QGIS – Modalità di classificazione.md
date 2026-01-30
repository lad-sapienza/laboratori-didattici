
In **QGIS → Proprietà layer → Simbologia → Graduato**, le **modalità di classificazione**
servono a dividere i valori numerici di un attributo in **classi**, a cui associare colori o simboli.
Le differenze riguardano **come vengono costruiti i confini delle classi**.

Per confrontarle useremo sempre lo stesso esempio:

**Valori di un campo (es. “numero reperti per sito”):**  
`1, 2, 2, 3, 4, 5, 7, 10, 20, 50`

---

## 1. Conteggio uguale (Quantile)

📌 **Ogni classe contiene lo stesso numero di elementi**

Con **5 classi**, ogni classe ha **2 elementi**.

**Esempio**
- Classe 1: `1 – 2`
- Classe 2: `2 – 3`
- Classe 3: `4 – 5`
- Classe 4: `7 – 10`
- Classe 5: `20 – 50`

**Pro**
- Tutti i colori vengono utilizzati
- Ottimo per confronti relativi (percentili)

**Contro**
- Intervalli irregolari
- Valori simili possono finire in classi diverse

**Quando usarlo**  
Distribuzioni sociali, economiche, ranking.

---

## 2. Deviazione standard

📌 Classi costruite **intorno alla media**, usando la deviazione standard.

**Esempio (schema tipico)**
- `< −1σ`
- `−1σ – media`
- `media – +1σ`
- `> +1σ`

**Cosa evidenzia**
- Valori “normali”
- Valori anomali (outlier)

**Pro**
- Molto informativa dal punto di vista statistico

**Contro**
- Poco intuitiva per un pubblico non tecnico
- Funziona meglio con distribuzioni quasi normali

**Quando usarla**  
Analisi esplorative, outlier, densità.

---

## 3. Intervalli naturali (Natural Breaks / Jenks)

📌 Le classi sono create **minimizzando la variabilità interna**  
QGIS individua i “salti naturali” nei dati.

**Esempio**
- `1 – 3`
- `4 – 7`
- `10`
- `20`
- `50`

**Pro**
- Classi molto aderenti alla distribuzione reale
- Mappa visivamente equilibrata

**Contro**
- Dipende fortemente dal dataset
- Poco confrontabile tra mappe diverse

**Quando usarla**  
Dati irregolari, fenomeni naturali, archeologia.

---

## 4. Intervallo fisso

📌 Le classi hanno **ampiezza costante**, definita dall’utente.

**Esempio (intervallo = 10)**
- `0 – 10`
- `10 – 20`
- `20 – 30`
- `30 – 40`
- `40 – 50`

**Pro**
- Controllo totale
- Ideale per confronti nel tempo o tra aree

**Contro**
- Possibili classi vuote
- Poco adattivo

**Quando usarla**  
Serie temporali, soglie normative, standard condivisi.

---

## 5. Intervallo uguale

📌 L’intero range è diviso in **parti uguali automaticamente**.

Range = 1 → 50  
5 classi → ampiezza ≈ 9.8

**Esempio**
- `1 – 10.8`
- `10.8 – 20.6`
- `20.6 – 30.4`
- `30.4 – 40.2`
- `40.2 – 50`

**Pro**
- Metodo semplice e oggettivo

**Contro**
- Poco efficace se i dati sono concentrati

**Quando usarla**  
Distribuzioni uniformi, didattica.

---

## 6. Pretty breaks

📌 Simile all’intervallo uguale, ma con **numeri arrotondati e leggibili**.

**Esempio**
- `0 – 10`
- `10 – 20`
- `20 – 30`
- `30 – 40`
- `40 – 50`

**Pro**
- Ottima leggibilità
- Adatta a mappe finali e pubblicazioni

**Contro**
- Meno precisa dal punto di vista analitico

**Quando usarla**  
Cartografia divulgativa e comunicativa.

---

## 7. Scala logaritmica

📌 Applica una trasformazione logaritmica ai dati **prima della classificazione**.

**Valori originali**
`1, 2, 5, 10, 20, 50, 500`

**Valori logaritmici (circa)**
`0, 0.3, 0.7, 1, 1.3, 1.7, 2.7`

**Pro**
- Gestisce forti asimmetrie
- Rende leggibili anche i valori piccoli

**Contro**
- Meno intuitiva
- Non funziona con valori ≤ 0

**Quando usarla**  
Densità, conteggi, distribuzioni molto sbilanciate.

---

## Riepilogo

| Metodo              | Idea chiave                | Usalo se…                |
| ------------------- | -------------------------- | ------------------------ |
| Quantile            | Stesso numero di oggetti   | confronto relativo       |
| Deviazione standard | Distanza dalla media       | anomalie                 |
| Natural breaks      | Struttura interna dei dati | dati irregolari          |
| Intervallo fisso    | Classi standard            | confronti                |
| Intervallo uguale   | Range diviso               | semplicità               |
| Pretty breaks       | Numeri leggibili           | pubblicazione            |
| Scala logaritmica   | Riduce asimmetria          | valori molto sbilanciati |
