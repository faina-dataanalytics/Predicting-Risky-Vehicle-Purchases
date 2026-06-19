# Car Auction Fraud Detection – Machine Learning Project

Dieses Projekt entwickelt ein Klassifikationsmodell zur Vorhersage von potenziell schlechten Fahrzeugkäufen („Bad Buys“) im Rahmen von Autoauktionen. Ziel ist es, finanzielle Risiken zu reduzieren, indem Fahrzeuge mit hohem Verlustpotenzial frühzeitig erkannt werden.

---

## Projektüberblick

Der Datensatz enthält historische Auktionsdaten mit technischen Merkmalen, Preisangaben, Zustandsinformationen und Käuferverhalten.  
Die Zielvariable **IsBadBuy** ist stark unausgewogen, weshalb der Schwerpunkt auf einem **hohen Recall** liegt: riskante Fahrzeuge sollen möglichst nicht übersehen werden.

Das Projekt umfasst:

- Explorative Datenanalyse (EDA)
- Datenbereinigung und Feature Engineering
- Modelltraining und -auswahl
- Evaluierung anhand von Precision und Recall
- Erstellung einer reproduzierbaren Pipeline
- Finaler Bericht für den Auftraggeber

---

## Repository-Struktur

01_projectmanagement/  
└── Project_Brief.md          # Aufgabenstellung, Projektziele

02_data/  
└── Data_Description.md       # Beschreibung der Features (keine Rohdaten)

03_scripts/  
├── data_preparation.py       # Bereinigung, Imputation, Normalisierung
├── feature_engineering.py    # Neue Features, Preisrelationen, Zeitmerkmale
├── modeling.py               # Training verschiedener Modelle
├── evaluation.py             # Metriken, Vergleich, Modellselektion
└── pipeline.ipynb            # Reproduzierbarer Workflow (optional)

04_analysis/  
└── Final_Report_for_Client.md # Geschäftlich orientierter Abschlussbericht

05_visual/  
└── plots/                    # Wichtige Visualisierungen (EDA, Importances)

README.md
requirements.txt


---

## Datenaufbereitung

Die Daten wurden umfassend bereinigt:

- Vereinheitlichung und Korrektur kategorialer Werte  
- Umwandlung von *PurchDate* in Datumsmerkmale  
- Behandlung ungültiger MMR-Werte (0,0 → NaN)  
- Entfernung irrelevanter und hochkardinaler Spalten  
- Normalisierung ausgewählter Kategorien (Color, Transmission, TopThreeAmericanName)  
- Imputation numerischer und kategorialer Werte  
- Keine Resampling-Methoden, da kein Leistungsgewinn (stattdessen `class_weight='balanced'`)

---

## Feature Engineering

Zur Verbesserung der Modellleistung wurden neue Merkmale erstellt:

- Zeitmerkmale: Kaufjahr, Monat, Wochentag  
- Normalisierte Laufleistung (*OdoPerYear*)  
- Preisrelationen: PriceToMMR, MMRDelta, MMRRatio  
- Relative Garantiekennzahl (*WarrantyRatio*)  
- Reduktion des ZIP-Codes auf drei Stellen (*ZIP3*)  
- Entfernung nicht mehr benötigter Rohspalten  

Diese Features helfen, nichtlineare Muster und Preisabweichungen besser zu erkennen.

---

## Modellierung

Trainierte Modelle:

- Baseline Logistic Regression  
- Optimierte logistische Regression  
- Logistic Regression mit PCA  
- Random Forest  
- k-Nearest Neighbors  

Bewertung anhand von:

- **Precision** (Vermeidung unnötiger Kosten)
- **Recall** (Erkennung riskanter Fahrzeuge – geschäftlich entscheidend)

Die besten Ergebnisse lieferten Random Forest und die optimierte logistische Regression.

---

## Ergebnisse

- Resampling-Methoden (Oversampling, Undersampling, SMOTE) verbesserten die Metriken nicht  
- `class_weight='balanced'` erzielte gleiche oder bessere Ergebnisse ohne künstliche Daten  
- Das finale Modell zeigt robuste Leistung bei der Erkennung von Bad Buys  
- Die Pipeline ist vollständig reproduzierbar und einsatzbereit

Der vollständige Abschlussbericht befindet sich unter:
- 04_analysis/Final_Report_for_Client.md

