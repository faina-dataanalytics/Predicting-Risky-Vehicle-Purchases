# Final Report – Car Auction Fraud Detection

## Zusammenfassung
Das entwickelte Modell unterstützt die Identifikation potenziell riskanter Fahrzeugkäufe. Durch gezielte Datenbereinigung, Feature Engineering und Modelloptimierung konnte ein robustes Klassifikationsmodell erstellt werden, das besonders auf einen hohen Recall ausgelegt ist.

## 1. Datenaufbereitung
- Vereinheitlichung und Korrektur kategorialer Werte  
- Umwandlung von *PurchDate* in Datumsmerkmale  
- Behandlung ungültiger MMR-Werte (0,0 → NaN)  
- Entfernung irrelevanter und hochkardinaler Spalten  
- Normalisierung ausgewählter Kategorien (Color, Transmission, TopThreeAmericanName)  

## 2. Feature Engineering
- Ableitung von Zeitmerkmalen (Jahr, Monat, Wochentag)  
- Normalisierung der Laufleistung (*OdoPerYear*)  
- Erstellung von Preisrelationen (PriceToMMR, MMRDelta, MMRRatio)  
- Relative Garantiekennzahl (*WarrantyRatio*)  
- Reduktion des ZIP-Codes auf drei Stellen  

Diese Merkmale verbessern die Erkennung nichtlinearer Muster und erhöhen die Modellstabilität.

## 3. Modellierung
Es wurden mehrere Modelle trainiert:
- Baseline Logistic Regression  
- Optimierte logistische Regression  
- Logistic Regression mit PCA  
- Random Forest  
- k-Nearest Neighbors  

Die Modelle wurden anhand von Precision und Recall bewertet.  
Der Fokus lag auf einem möglichst hohen Recall, um riskante Fahrzeuge zuverlässig zu erkennen.

## 4. Ergebnisse
- Random Forest und optimierte logistische Regression lieferten die besten Ergebnisse  
- Resampling-Methoden (Oversampling, Undersampling, SMOTE) führten zu keiner Verbesserung und wurden verworfen  
- *class_weight='balanced'* erwies sich als beste Strategie für unausgewogene Daten  

## 5. Empfehlung
Das finale Modell kann in den Einkaufsprozess integriert werden, um riskante Fahrzeuge frühzeitig zu markieren.  
Eine Erweiterung um Boosting-Modelle oder zusätzliche externe Datenquellen könnte die Leistung weiter verbessern.

## 6. Bereitgestellte Artefakte
- Vollständige Datenpipeline  
- Skripte für Datenaufbereitung, Feature Engineering und Modelltraining  
- Dokumentation der wichtigsten Erkenntnisse  
