# Airbnb a Catania: analisi del mercato degli affitti brevi

🇮🇹 Italiano · [🇬🇧 English](#airbnb-in-catania-analysis-of-the-short-term-rental-market)

Progetto finale del corso di **Data Analysis**. Analizziamo gli annunci Airbnb di Catania (4.669 annunci) con i dati pubblici di [Inside Airbnb](https://insideairbnb.com/get-the-data/) per capire come si distribuisce il mercato, quanto pesa la posizione sul prezzo e quali strutture lavorano di più.

## Domande a cui risponde l'analisi

- Come sono composti gli annunci per **tipologia** (appartamenti interi, camere private) e per **dimensione** (piccoli 1-2 ospiti, medi 3-4, grandi 5+)?
- Quanto cambia il **prezzo** tra le classi di dimensione?
- Quanto conta la **vicinanza al centro** sul prezzo e sulle recensioni?
- Come sono cambiate **domanda e offerta** dal 2015, e quanto è stagionale il mercato?
- Quali strutture hanno **lavorato di più nell'ultimo anno** e dove si trovano?

## Risultati principali

- **Mercato dominato dagli appartamenti interi**: 72,6% degli annunci, contro il 27,3% di stanze private. Wi-Fi, aria condizionata e cucina sono presenti in oltre l'80% degli annunci.
- **Il turismo si concentra nel centro**: circa il 61% degli annunci è entro 1 km da Piazza Duomo e circa il 78% delle recensioni arriva da lì. Il sovrapprezzo del centro, a parità di dimensione, è però modesto (mediana +2-8% entro 1,5 km).
- **La dimensione fa il prezzo**: mediana di 82 USD (piccoli), 93 (medi) e 134 (grandi) a notte, esclusi gli annunci sopra i 500 USD.
- **Mercato stagionale e in crescita**: circa il 76% delle recensioni annuali arriva tra aprile e ottobre. Dal 2015 le recensioni crescono di circa ×31 e gli annunci di circa ×29, ma dal 2022 è l'offerta a correre.
- **Pochi annunci fanno molta attività**: nell'ultimo anno è attivo il 57,7% degli annunci e il 10% più attivo produce oltre la metà delle recensioni.

La lettura completa dei risultati è nell'ultima sezione del notebook (*13. Lettura Conclusiva*).

## Contenuto del notebook

| Sezione | Argomento |
|---|---|
| 0-1 | Caricamento, pulizia e controllo dei dati |
| 2 | Casi sospetti e classi di dimensione |
| 3-4 | Prezzi per classe di dimensione |
| 5-6 | Analisi geospaziale e mappa interattiva |
| 7 | Performance (recensioni come proxy della domanda) |
| 8 | Analisi temporale e stagionalità |
| 9 | Distribuzione dei prezzi e outlier |
| 10-11 | Catania nel contesto regionale e composizione del mercato |
| 12 | Strutture che lavorano di più nell'ultimo anno (heatmap e mappe annuali) |
| 13 | Lettura conclusiva |

## Dati

I dati **non sono inclusi** nel repository. Scaricateli da [Inside Airbnb](https://insideairbnb.com/get-the-data/) (sezione Sicilia, file `listings.csv` e `reviews.csv`) e salvateli nella cartella `data/`:

```
data/
├── listings.csv
└── reviews.csv
```

L'analisi usa i dati relativi a Catania (`neighbourhood_cleansed == "Catania"`). L'ultima recensione presente nei file è del 28/09/2026, e i risultati possono cambiare con una versione più recente.

Fonte: Inside Airbnb, licenza [Creative Commons CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Come eseguire il progetto

1. Clonate il repository e inserite i due file in `data/`.
2. Installate le librerie:
   ```bash
   pip install pandas numpy matplotlib seaborn folium jupyter
   ```
3. Aprite il notebook e, nella prima cella, sostituite il caricamento da Google Drive con i percorsi locali:
   ```python
   listings = pd.read_csv("data/listings.csv")
   reviews = pd.read_csv("data/reviews.csv")
   ```
4. Eseguite tutte le celle, dall'alto in basso. Le celle vanno eseguite in ordine perché ogni sezione usa le variabili create prima.

Il notebook è nato in Google Colab: se lo aprite lì, montate Drive e lasciate i percorsi originali.

## Limiti dell'analisi

- Le **recensioni sono un proxy** della domanda, non misurano le prenotazioni né l'occupazione.
- Gli **annunci chiusi** non compaiono nei dati attuali: l'offerta storica è ricostruita dall'anno della prima recensione e può essere sottostimata (survivorship bias).
- Il **2026 è incompleto** (i dati arrivano a settembre) e per questo è escluso dai confronti tra anni.
- I **prezzi mancanti** (circa 385 annunci) e gli **outlier** sopra i 500 USD sono segnalati con dei flag, non eliminati, e sono esclusi dai confronti sui prezzi.
- Le **posizioni degli annunci** sono approssimate da Airbnb per tutelare la privacy degli host.

## Strumenti

Python, pandas, NumPy, matplotlib, seaborn, folium.

## Autori

Progetto del corso di Data Analysis, anno accademico 2026/27.

- Francesco Ruggeri
- Pierfrancesco Blancato
- Marco Ventimiglia
- Diego Valenti

## Licenza

Questo repository è pubblicato **solo a scopo di consultazione**. Il codice e i testi del progetto sono degli autori e non possono essere copiati, modificati o ridistribuiti senza il loro permesso. I dati restano soggetti alla licenza CC BY 4.0 di Inside Airbnb.

---

# Airbnb in Catania: analysis of the short-term rental market

[🇮🇹 Italiano](#airbnb-a-catania-analisi-del-mercato-degli-affitti-brevi) · 🇬🇧 English

Final project for the **Data Analysis** course.

We analyse the Airbnb listings of Catania (4,669 listings) using the public data from [Inside Airbnb](https://insideairbnb.com/get-the-data/), to understand how the market is distributed, how much location affects price and which properties perform best.

## Questions the analysis answers

- How are the listings composed by **type** (entire homes, private rooms) and by **size** (small 1-2 guests, medium 3-4, large 5+)?
- How much does the **price** change between size classes?
- How much does **proximity to the centre** matter for price and reviews?
- How have **demand and supply** evolved since 2015, and how seasonal is the market?
- Which properties **performed best over the last year** and where are they?

## Main results

- **The market is dominated by entire homes**: 72.6% of listings, against 27.3% private rooms. Wi-Fi, air conditioning and a kitchen are present in over 80% of listings.
- **Tourism is concentrated in the centre**: about 61% of listings are within 1 km of Piazza Duomo and about 78% of reviews come from there. The centre's price premium, for the same size class, is however modest (median +2-8% within 1.5 km).
- **Size drives price**: median of 82 USD (small), 93 (medium) and 134 (large) per night, excluding listings above 500 USD.
- **A seasonal and growing market**: about 76% of yearly reviews arrive between April and October. Since 2015 reviews have grown by about ×31 and listings by about ×29, but since 2022 it is supply that has been growing faster.
- **A few listings generate a lot of activity**: over the last year 57.7% of listings are active and the top 10% produce more than half of the reviews.

The full reading of the results is in the last section of the notebook (*13. Lettura Conclusiva*, in Italian).

## Notebook contents

| Section | Topic |
|---|---|
| 0-1 | Data loading, cleaning and checks |
| 2 | Suspicious cases and size classes |
| 3-4 | Prices by size class |
| 5-6 | Geospatial analysis and interactive map |
| 7 | Performance (reviews as a proxy for demand) |
| 8 | Time analysis and seasonality |
| 9 | Price distribution and outliers |
| 10-11 | Catania in the regional context and market composition |
| 12 | Best-performing listings over the last year (heatmap and yearly maps) |
| 13 | Concluding remarks |

The notebook text and chart labels are in Italian.

## Data

The data is **not included** in the repository. Download it from [Inside Airbnb](https://insideairbnb.com/get-the-data/) (Sicily section, files `listings.csv` and `reviews.csv`) and save it in the `data/` folder:

```
data/
├── listings.csv
└── reviews.csv
```

The analysis uses the data for Catania (`neighbourhood_cleansed == "Catania"`). The most recent review in the files is dated 28/09/2026, and results may change with a more recent version.

Source: Inside Airbnb, [Creative Commons CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) licence.

## How to run the project

1. Clone the repository and place the two files in `data/`.
2. Install the libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn folium jupyter
   ```
3. Open the notebook and, in the first cell, replace the Google Drive loading with local paths:
   ```python
   listings = pd.read_csv("data/listings.csv")
   reviews = pd.read_csv("data/reviews.csv")
   ```
4. Run all the cells from top to bottom. The cells must be run in order because each section uses variables created earlier.

The notebook was written in Google Colab: if you open it there, mount Drive and keep the original paths.

## Limitations of the analysis

- **Reviews are a proxy** for demand: they do not measure bookings or occupancy.
- **Closed listings** do not appear in the current data: historical supply is reconstructed from the year of the first review and may be underestimated (survivorship bias).
- **2026 is incomplete** (the data runs to September) and is therefore excluded from year-to-year comparisons.
- **Missing prices** (about 385 listings) and **outliers** above 500 USD are marked with flags, not deleted, and are excluded from price comparisons.
- **Listing locations** are approximated by Airbnb to protect hosts' privacy.

## Tools

Python, pandas, NumPy, matplotlib, seaborn, folium.

## Authors

Project for the Data Analysis course, academic year 2026/27.

- Francesco Ruggeri
- Pierfrancesco Blancato
- Marco Ventimiglia
- Diego Valenti

## Licence

This repository is published **for viewing only**. The code and texts of the project belong to the authors and may not be copied, modified or redistributed without their permission. The data remains subject to Inside Airbnb's CC BY 4.0 licence.
