# 📝 PLAN: Supervised Learning – Interaktiv Lärkurs

> Implementeringsplan för omstrukturering av Lab_2_Supervised_Learning.ipynb till en interaktiv lärkurs för 16-åriga nybörjare.

---

## 🎯 Övergripande Mål

Omstrukturera den befintliga **Lab_2_Supervised_Learning.ipynb** (som är komplex och riktad mot universitetsstudenter) till en pedagogisk, interaktiv kurs på svenska för gymnasieelever utan ML-erfarenhet.

**Pedagogisk filosofi:**
1. **Se först** – Visuell förklaring innan kod
2. **Ändra något** – Slider/knapp för att ändra ett värde
3. **Se resultatet** – Plot uppdateras live
4. **Fråga** – Quiz för att förstå vad som hände
5. **Experimentera** – Testa egna idéer

---

## 📂 Kursstruktur

```
Supervised_Learning_lektioner/
├── Lab_3_Lektion_1_Vad_Ar_ML.ipynb              (45 min)
├── Lab_3_Lektion_2_Utforska_Iris.ipynb           (45 min)
├── Lab_3_Lektion_3_Trana_Modell.ipynb            (45 min)
├── Lab_3_Lektion_4_Confusion_Matrix.ipynb         (60 min)
├── Lab_3_Lektion_5_Fraud_Detection.ipynb          (60 min)
├── Lab_3_Facit.ipynb                               (Svar)
├── Lab_3_Lärarguide.md                             (Lärarguide)
├── Lab_3_Snabbguide_För_Elever.md                 (Elevguide)
└── PLAN_SupervisedLearning_Lärkurs.md              (Denna fil)
```

**Total kurs:** ~4.5–5 timmar undervisningstid

---

## 📖 Pedagogisk Progression

```
Lektion 1: "Vad är ML?"
   → Grundbegrepp: ML, Supervised, Features, Labels
   → Interaktiv: Blomma-slider, Scatterplot med dropdown

Lektion 2: "Utforska verklig data"
   → Pandas: head(), describe(), shape
   → Interaktiv: Statistik per art, Histogram, Scatterplot

Lektion 3: "Träna din första modell"
   → Beslutsträd, Train/Test split, Accuracy
   → Interaktiv: Split-slider, Träningsknapp, max_depth-slider

Lektion 4: "Mäta prestanda rätt"
   → Confusion Matrix, Precision, Recall, F1-score
   → Interaktiv: Heatmap, Precision/Recall-simulator

Lektion 5: "Lösa verkligt problem"
   → Fraud Detection, Klassoimbalans, Threshold, ROC
   → Interaktiv: Modell-jämförelse, Threshold-slider
```

---

## 🎮 Interaktiva Element per Lektion

### Lektion 1 (Vad är ML?)
- 🎚️ **Slider** för att bläddra genom 150 blommor
- 📊 **Dropdown-menyer** för X/Y-axel i scatterplot
- 📈 **Live scatterplot** uppdateras när features väljs

### Lektion 2 (Utforska Iris)
- 📋 **Dropdown** för att välja art och se statistik
- 📊 **Histogram-slider** för antal staplar
- 🗺️ **Scatterplot** med val av features och label-checkbox

### Lektion 3 (Träna modell)
- 🎚️ **Split-slider** (10-50% testdata)
- ▶️ **Träningsknapp** för att starta träning
- 🌳 **max_depth-slider** (1-10) med live beslutsträd
- 🔮 **4 sliders** för att testa egna blomma-mätningar

### Lektion 4 (Confusion Matrix)
- 🔥 **Heatmap** av confusion matrix (uppdateras med max_depth)
- 📊 **Precision/Recall/F1-stapeldiagram** per klass
- 🎮 **TP/FP/FN/TN-sliders** för att simulera egna scenarios
- 🧪 **Experimentwidget** med criterion-dropdown och min_leaf-slider

### Lektion 5 (Fraud Detection)
- 🔄 **Träningsknapp** per modell-typ
- 📊 **Modell-jämförelse** via dropdown (5 modeller)
- 🎚️ **Threshold-slider** (0.01-0.99) med live confusion matrix
- 📈 **ROC-kurva** för alla modeller jämfört

---

## 🛠️ Tekniska Val

### Bibliotek
- `ipywidgets` – Alla interaktiva element (sliders, dropdowns, knappar, Output-widgets)
- `matplotlib` – Grafer och visualiseringar
- `seaborn` – Confusion matrix heatmap (snyggt med `sns.heatmap`)
- `pandas` – Datahantering
- `sklearn` – ML-modeller och metrics

### Modeller som används
- `DecisionTreeClassifier` – Enkel, visualiserbar, perfekt för nybörjare
- `RandomForestClassifier` – Lektion 5, bättre än enstaka träd
- `LogisticRegression` – Lektion 5, klassisk baseline

### Dataset
- **Iris** (sklearn.datasets.load_iris) – Lektionerna 1-4
- **Credit Card Fraud** (Kaggle via URL) – Lektion 5

---

## 📊 Scaffolding

### Quiz-frågor (totalt 50+)
| Lektion | Antal quiz-frågor |
|---------|------------------|
| Lektion 1 | 5 frågor |
| Lektion 2 | 8 frågor |
| Lektion 3 | 10 frågor |
| Lektion 4 | 12 frågor |
| Lektion 5 | 15 frågor |
| **Totalt** | **50 frågor** |

### Tabellövningar
- Lektion 1: Features vs Labels-tabell
- Lektion 2: Statistik per art (min/max/medel)
- Lektion 3: Accuracy-tabell per max_depth
- Lektion 4: Precision/Recall per klass
- Lektion 5: Modell-jämförelsetabell

---

## 📚 Supportdokument

### Lab_3_Lärarguide.md
- Lektionsstruktur med tidsindelning
- Tips för varje del
- Vanliga problem och lösningar
- Svar på alla 50+ quiz-frågor
- Differentieringsmöjligheter
- Diskussionsfrågor

### Lab_3_Facit.ipynb
- Kör och visar alla korrekta svar
- Beräknade statistik-tabeller
- Fullständiga modell-analyser

### Lab_3_Snabbguide_För_Elever.md
- ML-ordbok
- Viktiga kod-rader
- Confusion matrix förklarat
- Threshold-förklaring
- Vanliga problem och lösningar

---

## ✅ Checklista

- [x] Kursplan skapad (denna fil)
- [x] Lektion 1: Vad är Machine Learning?
- [x] Lektion 2: Utforska Iris-datasetet
- [x] Lektion 3: Träna din första modell
- [x] Lektion 4: Confusion Matrix och Evaluering
- [x] Lektion 5: Fraud Detection – Verkligt Problem
- [x] Lab_3_Facit.ipynb (alla svar)
- [x] Lab_3_Lärarguide.md (lärardokument)
- [x] Lab_3_Snabbguide_För_Elever.md (elevdokument)

---

## 🔗 Källmaterial

- **Originalnotebok:** `Lab_2_Supervised_Learning.ipynb` (David Bergström & Mattias Tiger, LiU)
- **Iris-dataset:** `sklearn.datasets.load_iris` (klassisk ML-benchmark)
- **Fraud-dataset:** Kaggle Credit Card Fraud Detection (Andrea Dal Pozzolo et al.)

---

*Licens: CC BY-NC-SA 4.0 – https://creativecommons.org/licenses/by-nc-sa/4.0/*
