# 📚 Lärarguide – Lab 3: Supervised Learning

> **Detaljerad guide för lärare som genomför laborationen "Supervised Learning – Interaktiv lärkurs"**

---

## 📋 Innehållsförteckning

1. [Om kursen](#om-kursen)
2. [Tekniska förberedelser](#tekniska-förberedelser)
3. [Lektion 1 – Vad är Machine Learning?](#lektion-1--vad-är-machine-learning)
4. [Lektion 2 – Utforska Iris-datasetet](#lektion-2--utforska-iris-datasetet)
5. [Lektion 3 – Träna din första modell](#lektion-3--träna-din-första-modell)
6. [Lektion 4 – Confusion Matrix och Evaluering](#lektion-4--confusion-matrix-och-evaluering)
7. [Lektion 5 – Fraud Detection](#lektion-5--fraud-detection)
8. [Svar på alla quiz-frågor](#svar-på-alla-quiz-frågor)
9. [Vanliga problem och lösningar](#vanliga-problem-och-lösningar)
10. [Differentieringsmöjligheter](#differentieringsmöjligheter)
11. [Övergripande tips](#övergripande-tips)

---

## Om kursen

### Vad är denna kurs?

Laborationen introducerar 16-åriga gymnasieelever till **Supervised Machine Learning** – ett av de viktigaste och mest använda områdena inom AI. Eleverna börjar med grundläggande begrepp och avslutar med att lösa ett verkligt problem: kreditkorts-bedrägeri-detektion.

Kursen är baserad på originalversionen av **David Bergström & Mattias Tiger, mattias.tiger@liu.se**, förenklad och omstrukturerad för nybörjare på svenska.

### Målgrupp

- **Ålder:** 15–17 år (gymnasieelever)
- **Förkunskaper:** Lite Python är ett plus men inte nödvändigt
- Fokus på **interaktivitet** – elever experimenterar, inte bara läser

### Tidsåtgång

| Lektion | Namn | Tid (ca) |
|---------|------|----------|
| Lektion 1 | Vad är Machine Learning? | 45 min |
| Lektion 2 | Utforska Iris-datasetet | 45 min |
| Lektion 3 | Träna din första modell | 45 min |
| Lektion 4 | Confusion Matrix och Evaluering | 60 min |
| Lektion 5 | Fraud Detection – Verkligt Problem | 60 min |
| **Totalt** | | **~4,5–5 timmar** |

### Vad eleverna lär sig

- Vad Machine Learning är och hur det skiljer sig från traditionell programmering
- Supervised vs Unsupervised vs Reinforcement Learning
- Hur man laddar och utforskar dataset med Pandas
- Beslutsträd som klassificeringsmodell
- Train/Test split och varför det är viktigt
- Confusion Matrix och evalueringsmåtten Precision, Recall, F1
- Klassoimbalans och hur man hanterar det
- ROC-kurvor och threshold-justering

### Licens

CC BY-NC-SA 4.0 – Laborationen är fri att använda, dela och modifiera.

---

## Tekniska förberedelser

### Vad du behöver

- Eleverna behöver **Google-konton** (för Google Colab)
- **Internetanslutning** (Colab kräver internet, och Lektion 5 laddar data från nätet)
- En webbläsare (Chrome rekommenderas)

### Bibliotek som används

Alla bibliotek är **förinstallerade på Google Colab** – inget behöver installeras manuellt.

| Bibliotek | Användning |
|-----------|-----------|
| `numpy` | Matematiska beräkningar |
| `pandas` | Datahantering i tabeller |
| `matplotlib` | Rita diagram och grafer |
| `seaborn` | Statistiska visualiseringar |
| `ipywidgets` | Interaktiva sliders, dropdowns, knappar |
| `sklearn` | Machine learning-modeller och verktyg |

### Innan lektionen

1. **Testa notebooken** – kör igenom hela laborationen själv
2. **Öppna notebooken på GitHub** och kontrollera Colab-länken i toppen
3. **Förbered förklaringar** för de viktigaste begreppen
4. Påminn eleverna om att **spara en kopia** i sin Google Drive

### Viktigt om Colab

- Eleverna måste **spara en kopia** (`Arkiv → Spara en kopia på Drive`)
- Annars förlorar de sitt arbete!
- Sessionen timeout:ar efter ca 90 minuter inaktivitet – eleverna måste starta om om de tar lång paus

---

## Lektion 1 – Vad är Machine Learning?

### Pedagogiska mål

- Förstå vad ML är och vad det används till
- Skilja Supervised, Unsupervised och Reinforcement Learning
- Förstå Features och Labels

### Lektionsstruktur (45 min)

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Introduktion: Vad är ML? Spam-filter-exemplet |
| 5–15 min | Del 2: Supervised Learning förklarat |
| 15–25 min | Del 3: Klassificering – Iris-blommor |
| 25–35 min | Del 4: Dataset-konceptet, Features vs Labels |
| 35–45 min | Del 5: Interaktiv demo med blomma-slider |

### Tips för introduktionen (Del 1)

- **Börja med frågan:** "Hur vet din telefon vem som ringer?"
- **Använd spam-filtret** som ett konkret exempel alla känner till
- **Rita på tavlan:** Input → ML-modell → Output
- Fråga eleverna: "Kan ni ge ett annat exempel på ML i vardagen?"

### Vanliga missförstånd (Del 2)

- Elever tror att ML är "smartare" än annan programmering – förklara att det är matematisk optimering
- Skillnaden Supervised/Unsupervised kan vara förvirrande – betona att "supervised" = vi ger märkta exempel

### Interaktiv del (Del 5)

Låt eleverna:
1. Dra slider för att se olika blommor
2. Välja features i scatterploten
3. Svara: "Vilka features verkar skilja arterna bäst?"

Svar: **petal_längd_cm** och **petal_bredd_cm** skiljer arterna tydligast.

---

## Lektion 2 – Utforska Iris-datasetet

### Pedagogiska mål

- Använda Pandas för dataexploration
- Förstå vad histogram och scatterplot visar
- Se och förstå klassbalans

### Lektionsstruktur (45 min)

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Repetition Lektion 1 |
| 5–15 min | Del 1: Ladda data, head(), describe() |
| 15–25 min | Del 2: Interaktiv statistik per art |
| 25–35 min | Del 3 & 4: Histogram och Scatterplot |
| 35–45 min | Del 5: Klassbalans + Quiz |

### Tips för Pandas-delen (Del 1 & 2)

- Förklara vad `describe()` returnerar – speciellt `std` (standardavvikelse)
- Låt eleverna fylla i tabellen i Övning 2.1 med faktiska värden
- Påpeka att `iris_df.shape` returnerar `(rader, kolumner)`

### Nyckelfynd eleverna ska göra

- **petal_längd_cm** skiljer BÄST mellan arterna (och petal_bredd_cm)
- **Setosa** har mycket mindre petals än de andra (1-2 cm vs 3-6 cm)
- Datasetet är perfekt **balanserat** (50 av varje art)

### Vanliga missuppfattningar

- Elever kan tro att fler kolumner = fler blommor. Påminn: rader = blommor, kolumner = mätningar
- "Standardavvikelse" kan vara nytt begrepp – förklara enkelt som "hur spridd datan är"

---

## Lektion 3 – Träna din första modell

### Pedagogiska mål

- Förstå beslutsträd intuitivt
- Göra Train/Test split
- Träna en modell och mäta accuracy
- Förstå overfitting

### Lektionsstruktur (45 min)

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Del 1: Vad är en modell? Beslutsträd |
| 5–20 min | Del 2: Train/Test split (slider-demo) |
| 20–35 min | Del 3 & 4: Träna och experimentera med max_depth |
| 35–45 min | Del 5: Förutsägelsewidget + Quiz |

### Tips för Beslutsträd (Del 1)

- **Rita trädet på tavlan!** Elever förstår visuellt bättre
- Gå igenom Quiz 3.1 muntligt med klassen
- Förklara att datorn "väljer" vilken feature att dela på automatiskt

### Tips för Train/Test Split (Del 2)

- Använd slider-demo och fråga: "Vad händer om vi har 90% testdata?"
- Analogin: "Skolprovet testar om du LÄRt dig – inte om du kan kopiera"
- Förklara `random_state=42` – för reproducerbarhet

### Tips för Overfitting (Del 4)

- Visa grafen "Accuracy vs max_depth"
- Fråga: "Vad händer med TRÄNING och TEST accuracy när max_depth ökar?"
- Viktigt insikt: Träning = 100% men Test = 70% = **overfitting**

### Nyckelfynd

- Optimal `max_depth` ≈ 3 för Iris
- `max_depth=1` underfittar (för enkel modell)
- `max_depth=10` overfittar (memorerar träningsdata)

---

## Lektion 4 – Confusion Matrix och Evaluering

### Pedagogiska mål

- Förstå vad Confusion Matrix visar
- Beräkna Precision och Recall
- Förstå trade-off:en mellan dem

### Lektionsstruktur (60 min)

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Del 1: Varför räcker inte accuracy? |
| 5–20 min | Del 2: Confusion Matrix interaktiv heatmap |
| 20–35 min | Del 3: Precision/Recall Simulator |
| 35–50 min | Del 4: Fullständig Iris-analys |
| 50–60 min | Del 5: Experimentera + Quiz |

### Tips för Accuracy-problemet (Del 1)

- **Starta med spam-exemplet:** 95% accuracy men hittar inget spam
- Låt eleverna svara Quiz 4.1 muntligt
- Fråga: "Kan ni tänka er ett annat fall där accuracy är missvisande?"

### Tips för Confusion Matrix (Del 2)

- Rita en 2×2 confusion matrix på tavlan
- Gå igenom varje cell: TP, TN, FP, FN
- Visa med verkliga tal från Iris-modellen

### Tips för Precision vs Recall (Del 3)

- **Medicinsk exempel är kraftfullt** – cancer vs spam-filter
- Låt elever använda simulatorn och observera trade-off:en
- Ställ frågan: "Vad föredrar du om du testades för en allvarlig sjukdom?"

### Nyckelfynd för Iris

- Setosa klassificeras **alltid rätt** (petal-värdena är unika)
- Versicolor och Virginica kan blandas ihop
- F1-score är det bästa samlade måttet

---

## Lektion 5 – Fraud Detection

### Pedagogiska mål

- Applicera alla lärdomar på ett verkligt problem
- Förstå klassoimbalans
- Jämföra modeller
- Använda threshold-justering

### Lektionsstruktur (60 min)

| Tid | Aktivitet |
|-----|-----------|
| 0–10 min | Del 1: Introduktion + ladda data |
| 10–20 min | Del 2 & 3: Visualisera obalansen, naiv modell |
| 20–35 min | Del 4: Jämför modeller (interaktivt) |
| 35–50 min | Del 5 & 6: Threshold-justering + ROC |
| 50–60 min | Avslut: Quiz + diskussion |

### Tips för datainladdning

- Datasettet laddas från internet – kan ta 30-60 sekunder
- Om internet inte fungerar: notebooken har fallback med syntetisk data
- Visa elever hur URL:en till datasetet ser ut

### Tips för Klassoimbalans (Del 1 & 3)

- **Starta med Quiz 5.1** – eleverna inser direkt problemet
- Visa visualiseringen av 99.8% vs 0.2%
- Analogin: "Hitta en röd godis i en skål med 578 gröna!"

### Tips för Threshold-justering (Del 5)

- Låt varje elev bestämma sin threshold och motivera
- Diskutera: Bank-perspektiv vs Kund-perspektiv
- Nyckelpunkt: Threshold 0 → Recall=100%, Precision=0.17%

### Avslutande diskussion

Frågor att diskutera med klassen:
1. "Vilken modell skulle ni välja för ert eget kreditkort?"
2. "Har AI-beslut etiska konsekvenser? (Felaktigt blockerat kort)"
3. "Hur kan vi göra ML-system mer rättvisa?"

---

## Svar på alla quiz-frågor

### Lektion 1

**Quiz 1.1:**
1. Netflix → Unsupervised Learning (alternativt Supervised om explicit betyg)
2. Robot som lär sig gå → Reinforcement Learning
3. Märkta röntgenbilder → Supervised Learning

**Quiz 1.2:**
1. Märkta exempel
2. Mönster
3. Svar för ny data

**Quiz 1.3:**
1. Huspriset → NEJ, det är Regression (förutsäger ett kontinuerligt tal)
2. Klasser: Setosa, Versicolor, Virginica
3. 4 features

### Lektion 2

**Quiz 2.1 (ungefärliga värden):**

| Art | petal_längd (medel) | petal_bredd (medel) |
|-----|-------------------|-------------------|
| setosa | 1.46 cm | 0.25 cm |
| versicolor | 4.26 cm | 1.33 cm |
| virginica | 5.55 cm | 2.03 cm |

**Quiz-frågorna:**
1. `iris_df.shape` → (150, 9) – 150 rader, 9 kolumner
2. Bästa feature: petal_längd_cm (setosa har 1-2 cm, andra har 3-7 cm)
3. Balanserat dataset = lika många per klass. Viktigt för att modellen inte ska favorisera en klass
4. Setosa separeras perfekt – tydlig kluster längst ned-vänster
5. std=0.43 → Relativt lite variation i sepal_bredd (värdena klustrar nära medelvärdet)
6. Bästa enstaka feature: petal_längd_cm (separerar Setosa perfekt, och ger bra separation för Versicolor/Virginica)
7. Viktigt att titta på data INNAN träning: Förstå struktur, hitta problem, välja rätt modell
8. sepal_längd vs sepal_bredd: Arterna **överlappar** – dåliga features för klassificering!

### Lektion 3

**Quiz 3.1 (beslutsträd):**
Blomma med petal_längd=4.5, petal_bredd=1.2:
1. petal_längd < 2.5? → NEJ
2. Höger väg
3. petal_bredd < 1.75? → JA
4. Förutsägelse: **VERSICOLOR**

**Övriga quiz-frågor:**
- Hyperparameter = inställning du väljer INNAN träning (max_depth). Parameter = lärt av modellen (tröskelvärden i trädet)
- Overfitting = hög tränings-accuracy, låg test-accuracy
- random_state=42 → Reproducerbarhet (alltid samma split)
- max_depth=1 → Kan bara göra en enda uppdelning – underfitting för komplexa problem
- Beslutsträd: Ställer JA/NEJ-frågor om features och navigerar ner till en klass
- 500 × 0.2 = 100 datapunkter i testset
- petal_längd från 1.5→5.0 → Modellen ändrar förutsägelse från Setosa till Versicolor/Virginica
- Testdata används INTE för träning – annars "fuskar" modellen (memorerar svaren)
- Accuracy = antal rätt / totalt antal × 100
- Optimal max_depth ≈ 3 (bäst test-accuracy utan overfitting)

### Lektion 4

**Quiz 4.1:**
1. 99.8% accuracy
2. Recall = 0% → Modellen hittar INGET bedrägeri → Värdelös!

**Quiz 4.2 (medicinsk):**
1. Recall = 15/(15+5) = **75%**
2. Precision = 15/(15+10) = **60%**
3. 75% recall för cancertest är problematiskt – missar 25% av sjuka patienter

**Övriga quiz-frågor:**
- TP = Setosa-blomma korrekt klassificerad som Setosa ✓
- Precision=100%, Recall=50% → Alla förutsägelser är rätt, men hittar bara hälften av Virginica
- Rad Versicolor=[0, 8, 2] → 2 Versicolor-blommor klassificerades som Virginica
- Diagonalen = TP per klass (rätt klassificerade)
- False Negative i cancer = Sjuk patient diagnoseras som frisk → Farligt!
- F1 = harmoniskt medel av Precision och Recall. Används när klasserna är obalanserade
- 95% accuracy, 10% fraud-recall → Dålig modell! Missar 90% av bedrägerier
- CM med max_depth=1 → Stora off-diagonal värden (många fel)
- Macro average = Genomsnitt per klass (viktas lika oavsett klasstorlek)
- Precision = Av allt modellen säger är X, hur rätt är det? Recall = Av allt som är X, hur mycket hittar modellen?
- Versicolor/Virginica blandas för att de har överlappande petal-värden. Setosa har unika (muito pequena) petals
- Precision=0% = Modellen förutsäger aldrig den klassen korrekt

### Lektion 5

**Quiz 5.1:**
1. Accuracy ≈ 99.83%
2. Recall = 0%
3. Värdelös modell – hittar inget bedrägeri!

**Övriga quiz-frågor:**
- Klassoimbalans = Stor skillnad i antal samples per klass. Problem: Modellen ignorerar ovanliga klassen
- 99.8% accuracy men hittar inget bedrägeri → Inte en bra modell!
- Threshold sänks 0.7→0.2 → Recall ökar (fler bedrägerier hittas), Precision sjunker (fler falskt alarm)
- Threshold för bank: Låg (0.2-0.4) – bättre med falskt alarm än missat bedrägeri
- ROC = kurva som visar True Positive Rate vs False Positive Rate för alla thresholds. AUC = area under kurvan (1.0 = perfekt, 0.5 = slumpmässig)
- class_weight='balanced' → Multiplicerar förlusten för ovanliga klasser → Modellen fokuserar mer på att hitta dem
- False Negative = Missat bedrägeri → Kunden drabbas av stöld
- False Positive = Falskt alarm → Kundens kort blockeras i onödan
- Precision = 50/1000 = **5%**
- Random Forest bättre: Kombinerar många träd → Minskar overfitting och variance
- Optimal threshold: Beror på bank-policy, vanligtvis 0.2-0.5
- Balanserat dataset = lika många per klass (som Iris). Obalanserat = stor skillnad (som Fraud)
- Threshold=0 → Alltid förutsäger bedrägeri. Recall=100%, Precision=0.17%
- Threshold=1 → Förutsäger aldrig bedrägeri. Recall=0%, Precision=undefined (0/0)
- De 3 viktigaste sakerna: (Elevsvar varierar – alla svar som reflekterar kursen är godkänna)

---

## Vanliga problem och lösningar

### Problem 1: Widgets visas inte

**Symptom:** Ipywidgets-cellerna kör men ingenting interaktivt visas  
**Lösning:**
1. Kontrollera att `import ipywidgets as widgets` körts
2. Kör cellen igen
3. Använd Chrome (inte Firefox/Safari)
4. Aktivera widgets: `from google.colab import output; output.enable_custom_widget_manager()`

### Problem 2: Lektion 5 kan inte ladda data

**Symptom:** `pd.read_csv(url)` ger fel  
**Lösning:**
1. Kontrollera nätanslutning
2. Notebooken har automatisk fallback med syntetisk data
3. Förklara för eleverna att den syntetiska datan har liknande egenskaper

### Problem 3: Kärnan kraschar ("Kernel died")

**Symptom:** Colab-kärnan slutar svara  
**Lösning:**
1. Kör `Runtime → Restart runtime`
2. Kör alla celler från början igen (Shift+F10)
3. Om det fortsätter: Minska datastorlek eller stäng andra flikar

### Problem 4: "NameError: name 'X_train' is not defined"

**Symptom:** Celler i lektion 3-5 ger NameError  
**Lösning:**
1. Imports-cellen och setup-cellen måste köras FÖRST
2. Kör alla celler uppifrån: `Runtime → Run all`

### Problem 5: Grafer visas inte

**Symptom:** Matplotlib-grafer visas inte  
**Lösning:**
1. Lägg till `%matplotlib inline` i importcellen
2. Kör cellen igen

---

## Differentieringsmöjligheter

### För elever som behöver mer stöd

- Fokusera på lektion 1-3 (grundbegrepp)
- Låt dem jobba med sliders och observera utan att förstå koden
- Ge konkreta analogier (spam-filter, Netflix, etc.)
- Tillåt pararbete

### För elever som vill gå längre

- Utforska fler hyperparametrar (min_samples_split, min_samples_leaf)
- Prova RandomForest och jämföra med beslutsträdet
- Undersöka varför petal-features fungerar bättre
- Läs om XGBoost (originalnotebooken använder detta)
- Utforska GridSearchCV för hyperparameter-sökning

### Extra utmaningar

1. **Ny feature-ingenjöring:** Kan du skapa en ny feature som kombinations-ratio av petal/sepal?
2. **Cross-validation:** Vad händer om vi delar data på 5 delar istället för 2?
3. **Annan modell:** Prova SVM (Support Vector Machine)
4. **Visualisera beslutet:** Rita beslutsregionerna för modellen

---

## Övergripande tips

### Håll eleverna engagerade

1. **Starta med frågor** – "Har ni fått ett spam-mail? Hur visste mailen att det var spam?"
2. **Visa verkliga applikationer** – ansiktsigenkänning, autonoma bilar, medicinsk diagnos
3. **Låt eleverna interagera** – sliders och knappar gör det roligt
4. **Fira förutsägelser** – när modellen gör rätt, fira med klassen

### Vanliga diskussionsfrågor

- "Är ML alltid rätt? Kan det vara fel? Vad händer då?"
- "Vem är ansvarig om en AI-modell gör fel i ett medicinskt system?"
- "Kan ML vara diskriminerande? Vad händer om träningsdatan är partisk?"

### Tidsbesparings-tips

- Om tidsbrist: Hoppa över Lektion 2 (utforska Iris) och gå direkt till Lektion 3
- Kör imports-cellen i förväg för att spara tid i klassen
- Demonstrera interaktiva delar på projicering, låt sedan eleverna experimentera själva

### Bedömning

Förslag på bedömningsfrågor:
1. "Förklara vad Train/Test split är och varför vi gör det" (Lektion 3)
2. "En modell har accuracy=99% men recall=5% för klassen 'bedrägeri'. Är den bra?" (Lektion 4-5)
3. "Vad är skillnaden mellan Precision och Recall?" (Lektion 4)
4. "Ge ett exempel på ett klassificeringsproblem och beskriv features och labels" (Lektion 1)
