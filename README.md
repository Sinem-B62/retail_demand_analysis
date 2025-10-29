# Retail Demand Forecasting (Prognose der Produktnachfrage)
---
Dieses Projekt entwickelt ein XGBoost-Modell, um die tägliche Produktnachfrage für Einzelhandelsfilialen in der Provinz Guayas vorherzusagen.

## 🎯 Business-Ziel

 **Problem:** Ungenaue Prognosen führen zu Überbeständen (hohe Kosten) oder Fehlbeständen (Umsatzverlust).
 
 **Lösung:** Ein ML-Modell zur Optimierung der Bestandsverwaltung durch präzise Tägliche-Prognosen auf Filial- und Artikelebene.

### **📋 Projekt-Scope & Fokus**

| **Parameter** | **Details**                                          |
| ------------- | ---------------------------------------------------- |
| **Region**    | Guayas (Provinz)                                     |
| **Produkte**  | Top 3 Familien: `GROCERY I`, `BEVERAGES`, `CLEANING` |
| **Zeitraum**  | Q1 2014 (Januar – März)                              |
| **Zielgröße** | `unit_sales` (Verkaufte Einheiten pro Tag)           |


### ⚙️ **Methodik & Prozess**
- Datenaufbereitung
  - EDA
   - Bereinigen (NaNs, Ausreißer)
   - Filtern der Rohdaten: Fokussierung auf die Region Guayas und die Top-3-Produktfamilien.
- Feature Engineering
  -  Erstellung von zeitbasierten Merkmalen (z.B. Wochentag, Monat).
  - Erstellung von Lag-Features (Verkäufe von lag_1, lag_7, lag_30).
  - Erstellung von rollierenden Statistiken (z.B. rolling_std_7).
- Modellierung (XGBoost)Validierung:
  - Chronologische Aufteilung (Training auf Jan/Feb, Test auf März).
  - Tracking:Einsatz von MLflow zur Protokollierung aller Experimente.
  - Optimierung: Hyperparameter-Tuning zur Steigerung der Modellgenauigkeit.
 
    
### 📈 **Ergebnisse & Herausforderungen** 
| **Modell**             | **Parameter**           | **Ergebnis**                                                         |
| ---------------------- | ----------------------- | -------------------------------------------------------------------- |
| **Baseline-Modell**    | Standard-Hyperparameter | Referenzwert für Fehler-Metrik (z. B. RMSE = 0.86)                   |
| **Optimiertes Modell** | Getunte Hyperparameter  | **Signifikante Reduzierung** des Prognosefehlers (z. B. RMSE = 0.81) |




**Wichtige Herausforderungen**
- Datenqualität: Korrekte Behandlung von Ausreißern und fehlenden Werten war entscheidend.

- Feature Engineering: Die Erstellung von Lag- und Rolling-Features war der Schlüssel zur Modellgenauigkeit.

- Reproduzierbarkeit: Sicherstellung konsistenter Ergebnisse durch random_state=42 und MLflow.

### **🛠️ Tech-Stack**

- Python
- Pandas
- XGBoost
- Scikit-learn
- MLflow

---

### 📚 Datenquelle

Die für diese Analyse verwendeten Rohdaten stammen aus dem Kaggle-Wettbewerb: **["Corporación Favorita Grocery Sales Forecasting"]**.

(https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data)

## 📘 Google Colab Notebooks

- 📊 **Datenaufbereitung & Feature Engineering**  
 [01_data_guayas_preprocessing.ipynb](https://colab.research.google.com/drive/1GWefzPzuUnXaa4HqD7xiq0RsD4Vk8D3n?usp=sharing)

- 🤖 **Modellierung & Evaluation**  
  [02_&_03_guayas_modeling_and_evaluation.ipynb]([https://colab.research.google.com/drive/2BcDeFgHiJkLmNoPqRsTuVwXyZa](https://colab.research.google.com/drive/18Ox2ScJpH1fP7JgzmbqQr1YytUAieSxV?usp=sharing))

