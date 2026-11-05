# Airbnb a Catania: analisi del mercato degli affitti brevi

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

- *Nome Cognome*
- *Nome Cognome*

## Licenza

Il codice è rilasciato con licenza MIT (aggiungete un file `LICENSE` se volete usarla). I dati restano soggetti alla licenza CC BY 4.0 di Inside Airbnb.
