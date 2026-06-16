# 🚀 Snabbguide för Elever – Lab 3: Supervised Learning

> **Allt du behöver för att klara laborationen – på en sida!**

---

## 🤖 Vad är Machine Learning?

> Machine Learning (ML) = Datorer lär sig från EXEMPEL, istället för att vi programmerar varje regel

**Tre typer:**
- **Supervised Learning** – Vi ger modellen märkta exempel (input + rätt svar)
- **Unsupervised Learning** – Modellen hittar mönster själv
- **Reinforcement Learning** – Modellen lär sig av belöning/straff

---

## 📖 Ordbok (ML-ord du behöver känna till)

| Ord | Förklaring | Iris-exempel |
|-----|-----------|-------------|
| **Feature** | En egenskap/mätning av datapunkten | Blommas petal-längd = 5.2 cm |
| **Label** | Det rätta svaret/kategorin | "Virginica" |
| **Sample / Datapunkt** | En rad i datasetet | En specifik blomma |
| **Dataset** | Alla datapunkter tillsammans | 150 iris-blommor |
| **Model** | Matematisk funktion som förutsäger | Beslutsträd |
| **Training** | Modellen lär sig från märkta exempel | Träna på 120 blommor |
| **Prediction** | Modellens gissning på ny data | "Setosa" |
| **Accuracy** | Andel rätt förutsägelser | 95% korrekt |
| **Overfitting** | Modellen memorerar träning, misslyckas på test | Träning 100%, Test 70% |
| **Hyperparameter** | Inställning du väljer INNAN träning | max_depth=3 |
| **Class / Klass** | En kategori att klassificera till | Setosa, Versicolor, Virginica |
| **Balanced dataset** | Lika många samples per klass | 50+50+50 = Iris |

---

## 🌸 Iris-datasetet i korthet

```
150 iris-blommor → 3 arter (klasser)
├── 50 × Setosa 🌸   (small, korta petals)
├── 50 × Versicolor 🌺 (mellanstor)
└── 50 × Virginica 🌻  (stor, långa petals)

4 features per blomma:
1. sepal_längd_cm   (kalkblad längd)
2. sepal_bredd_cm   (kalkblad bredd)
3. petal_längd_cm   (kronblad längd)  ← Viktigast!
4. petal_bredd_cm   (kronblad bredd)  ← Viktig!
```

💡 **Tips:** petal-längd och petal-bredd är de BÄSTA features för klassificering!

---

## 🔧 Viktiga kod-rader att känna till

### Ladda data
```python
from sklearn.datasets import load_iris
iris = load_iris()
X, y = iris.data, iris.target     # X = features, y = labels
```

### Utforska data med Pandas
```python
import pandas as pd
df = pd.DataFrame(X, columns=['sepal_l', 'sepal_w', 'petal_l', 'petal_w'])
df.head()      # Visa 5 första rader
df.describe()  # Statistik (min, max, medel, etc.)
df.shape       # (antal rader, antal kolumner)
```

### Train/Test Split
```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
# 80% träning, 20% test
```

### Träna en modell
```python
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier(max_depth=3)  # max_depth är hyperparameter
model.fit(X_train, y_train)                  # Träna!
```

### Gör förutsägelser och mät
```python
predictions = model.predict(X_test)

from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, predictions)
print(f"Accuracy: {accuracy:.1%}")
```

### Confusion Matrix
```python
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, predictions)
print(cm)
```

### Precision, Recall, F1
```python
from sklearn.metrics import precision_score, recall_score, f1_score
precision = precision_score(y_test, predictions, average='macro')
recall    = recall_score(y_test, predictions, average='macro')
f1        = f1_score(y_test, predictions, average='macro')
```

---

## 📊 Confusion Matrix – Vad betyder de fyra cellerna?

```
                  FÖRUTSATT
              Negativt    Positivt
FAKTISK  Neg  [ TN      |  FP  ]
         Pos  [ FN      |  TP  ]

TN = True Negative  → Korrekt negativ (legitimt mail = legitimt)
TP = True Positive  → Korrekt positiv (spam = spam)
FP = False Positive → Falskt alarm    (legitimt mail = spam!) ← Farligt för email
FN = False Negative → Missat positiv  (spam = legitimt mail)  ← Farligt för cancer
```

---

## 📏 Evalueringsmått i korthet

```
Accuracy  = (TP + TN) / Total          ← Hur ofta rätt?
Precision = TP / (TP + FP)             ← Av flaggade: hur många rätt?
Recall    = TP / (TP + FN)             ← Av alla rätta: hur många hittades?
F1-score  = 2 × (Precision × Recall) / (Precision + Recall)  ← Balanserat mått
```

**När används vad?**

| Situation | Viktigast | Varför |
|-----------|-----------|--------|
| Cancerdiagnos | **Recall** | Bättre falskt alarm än missa cancer |
| Spam-filter | **Precision** | Bättre missa spam än blockera viktigt mail |
| Fraud Detection | **Recall** | Bättre falskt alarm än missat bedrägeri |

---

## 🎚️ Threshold – Vad är det?

En modell returnerar en **sannolikhet** (0.0 – 1.0) för varje klass.

```
Sannolikhet = 0.35:
  Threshold = 0.5 → Klassificeras som NEGATIVT  (0.35 < 0.5)
  Threshold = 0.3 → Klassificeras som POSITIVT  (0.35 > 0.3)
```

**Trade-off:**
- **Låg threshold** → Mer Recall, Mindre Precision
- **Hög threshold** → Mer Precision, Mindre Recall

---

## ⚖️ Klassoimbalans – Vad är det?

Om klassen "bedrägeri" bara är 0.17% av datasetet:
- En dum modell kan nå 99.83% accuracy genom att **alltid säga "legitimt"**
- Men den hittar **0% bedrägerier**!

**Lösning:** Använd `class_weight='balanced'` eller välj låg threshold.

---

## 🌳 Beslutsträd – Intuitivt förklarat

```
          petal_längd < 2.5?
          /              \
        JA                NEJ
         |                 |
      SETOSA    petal_bredd < 1.75?
                /              \
              JA                NEJ
               |                 |
          VERSICOLOR          VIRGINICA
```

- `max_depth=1` → Bara ett beslut (underfitting)
- `max_depth=3` → Bra för Iris
- `max_depth=10` → Overfitting (memorerar träningsdata)

---

## 🆘 Vanliga problem och lösningar

| Problem | Lösning |
|---------|---------|
| Widgets visas inte | Prova Chrome istället för Firefox/Safari |
| NameError: X_train not defined | Kör imports- och setup-cellerna först! |
| Kernel died | Runtime → Restart runtime → Run all |
| Data laddas inte (Lektion 5) | Kontrollera internet, notebooken har fallback |
| Grafer visas inte | Lägg till `%matplotlib inline` i imports |

---

## 💡 Tips för att lyckas

1. **Kör cellerna uppifrån och ner** – hoppa inte runt
2. **Spara din kopia** – Arkiv → Spara en kopia på Drive
3. **Lös prova sliders** – Ändra värden och observera vad som händer
4. **Skriv ner dina svar** i quiz-cellerna – det hjälper dig att lära
5. **Fråga om du fastnar** – läraren och klasskamrater hjälper gärna!

---

## 🚀 Vill du lära dig mer?

- **Google Machine Learning Crash Course** (gratis, på engelska)
- **Kaggle Learn** – Interaktiva ML-kurser
- **3Blue1Brown** – Neurala nätverk förklarade visuellt (YouTube)
- **fast.ai** – Praktisk Deep Learning (lite mer avancerat)

---

*Lycka till! 🎓*
