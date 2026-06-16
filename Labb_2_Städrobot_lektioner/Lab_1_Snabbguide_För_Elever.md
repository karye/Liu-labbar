# 🤖 Snabbguide för elever – Städroboten

> **Välkommen till AI-kursen om Städroboten!**
> Du är på väg att lära dig hur AI fungerar – och du kommer att skriva riktig kod! 🚀

---

## 📋 Innehållsförteckning

1. [Vad du behöver veta innan du börjar](#vad-du-behöver-veta-innan-du-börjar)
2. [Snabbstartsguide – Steg för steg](#snabbstartsguide)
3. [Ordbok – viktiga begrepp](#ordbok)
4. [Vanliga frågor (FAQ)](#vanliga-frågor)
5. [Fuskblad – Python-syntax](#fuskblad)
6. [Resurser och hjälp](#resurser)

---

## 🧠 Vad du behöver veta innan du börjar

### 1. Vad är en Jupyter Notebook?

```
┌──────────────────────────────────┐
│  📄 Jupyter Notebook             │
│                                  │
│  ┌──────────────────────────┐    │
│  │  📝 Textruta              │    │
│  │  (Förklaring på svenska)  │    │
│  └──────────────────────────┘    │
│                                  │
│  ┌──────────────────────────┐    │
│  │  💻 Kodruta               │    │
│  │  print("Hej Robot!")      │    │
│  │  >>> Hej Robot!           │    │
│  └──────────────────────────┘    │
└──────────────────────────────────┘
```

- Det är ett **interaktivt dokument** med text och kod blandat
- Du läser förklaringarna i textrutan och **kör** koden i kodrutorna
- **Kör en cell:** Klicka på den och tryck `Shift+Enter` (eller klicka ▶ knappen)
- **Om något krånglar:** Kör cellen igen – eller kör om från toppen

> 💡 **Viktigt:** Kör alltid cellerna **uppifrån och ned** i rätt ordning!

---

### 2. Vad är en städrobot?

```
Världen (ett rutnät 10×10):

  0 1 2 3 4 5 6 7 8 9   ← x-axel
0 # # # # # # # # # #
1 # H . . ░ . . . . #
2 # . # . . . ░ . . #
3 # . . . . . . . . #
4 # . ░ . # . . . ░ #
5 # . . . . . . . . #
6 # # # # # # # # # #
↑
y-axel

H = Robotens hem (startposition)
░ = Smuts (det du ska städa)
# = Vägg (kan inte gå igenom)
. = Tom cell (kan gå här)
```

- En **virtuell robot** som bor i en rutnätsvärld
- Roboten kan röra sig: **Upp, Ner, Vänster, Höger**
- Roboten kan **Dammsuga** smuts
- Målet: **Städa all smuts** och **återvänd hem** med så FÅ rörelser som möjligt

---

### 3. Vad är programmering?

- Du ger **instruktioner till datorn**, steg för steg
- Datorn gör **exakt** vad du säger (inte mer, inte mindre)
- Du bestämmer **logiken** – vad som ska hända

```
Du skriver:          Datorn gör:
─────────────────    ──────────────────────
print("Hej!")    →   Skriver ut: Hej!
x = 5 + 3        →   Räknar ut: x = 8
```

> 🎯 **Kom ihåg:** Datorn är superdumm men supersnabb. DU måste tänka åt den!

---

### 4. Regler för den här kursen

| Regel | Varför |
|-------|--------|
| ✅ Läs instruktionerna **noggrant** | Annars missar du viktiga tips |
| ✅ Kör celler i **rätt ordning** | Koden beror på tidigare celler |
| ✅ Om något är fel – **läs felmeddelandet** | Det berättar vad som gick snett |
| ✅ **Experimentera!** Det är OK att göra fel | Det är så man lär sig |
| ✅ Fråga **läraren** om du sitter fast länge | Ingen ska sitta fast ensam |

---

## 🚀 Snabbstartsguide

**Steg 1:** Öppna laborationen i webbläsaren (Google Colab)

**Steg 2:** Läs rubriken och introduktionstexten

**Steg 3:** Kör den första kodcellen `Shift+Enter`

**Steg 4:** Se vad som händer! Titta på resultatet nedanför cellen

**Steg 5:** Läs förklaringen efter cellen

**Steg 6:** Gör övningarna (de börjar med **Uppgift 1.x.x**)

**Steg 7:** Svara på frågorna i texten (de börjar med **Fråga X**)

```
Laborationen är uppdelad i 4 delar:
┌─────────────────────────────────────────────────┐
│  Lab 1.0 – Rutnätsvärlden                        │
│  Lab 1.1 – Simulering (du styr roboten)          │
│  Lab 1.2 – Känd miljö (roboten styr sig själv)   │
│  Lab 1.3 – Okänd miljö (roboten utforskar)       │
│  Lab 1.4 – Lös okänd miljö (BFS-sökning)         │
└─────────────────────────────────────────────────┘
```

---

## 📖 Ordbok

| Ord | Vad det betyder |
|-----|-----------------|
| **Algoritm** | En steg-för-steg-instruktion för att lösa ett problem |
| **Agent** | Ett program som observerar sin omgivning och fattar beslut |
| **Perception / Percept** | Vad agenten "ser" eller "vet" just nu |
| **Simulering** | En virtuell värld i datorn |
| **Rutnät / Grid** | Världen uppdelad i små celler (som ett schackbräde) |
| **Vägg (`#`)** | En cell roboten **inte** kan gå igenom |
| **Smuts (`░`)** | Något roboten ska dammsuga |
| **Hem (`H`)** | Robotens startposition (dit den ska återvända) |
| **Poäng** | Score – hur bra roboten klarade uppdraget |
| **BFS** | Bredden-först-sökning – algoritm för kortaste vägen |
| **DFT** | Djupet-först-traversering – algoritm för att besöka allt |
| **NOOP** | No Operation – roboten gör ingenting |
| **Täckhet (density)** | Hur stor andel av rutorna som är väggar/smuts (0.0–1.0) |

---

## ❓ Vanliga frågor

### "Vad gör jag om cellen inte kör?"
1. Kontrollera att du har **markerat cellen** (klicka på den)
2. Försök med `Shift+Enter` igen
3. Om det fortfarande inte fungerar: Välj i menyn **Runtime → Restart runtime**, kör sedan om **alla** celler från toppen

### "Vad betyder det röda felmeddelandet?"
```
NameError: name 'generate_world' is not defined
```
👉 Du har **inte kört en tidigare cell** som definierar funktionen. Gå tillbaka och kör cellerna i ordning!

```
SyntaxError: invalid syntax
```
👉 Du har ett **stavfel** i koden. Läs rad-numret i felmeddelandet och hitta felet.

```
IndentationError: expected an indented block
```
👉 **Indenteringen** (mellanslag i början av raden) är fel. Python kräver exakt rätt antal mellanslag.

### "Var är min robot i världen?"
- Titta på rutnätsutskriften – roboten visas som `H` (hemma) eller `R` (på väg)
- Koordinaterna visas som `(x, y)` där `(1, 1)` är hörnet innanför ytterväggarna

### "Varför fastnar roboten?"
- Roboten kan ha **kört slut på plan** – kör fler steg
- Det kan finnas en **bugg i din kod** – läs felmeddelandet
- Roboten kan ha **fastnat i en loop** – starta om simuleringen

### "Är jag för långsam/snabb?"
- Det finns **ingen tidspress** – ta den tid du behöver
- Om du är snabb: kolla "Utmaningar" i slutet av varje del
- Om du är långsam: hoppa till nästa del och kom tillbaka

---

## 💻 Fuskblad – Python-syntax

### Skriva ut text
```python
print("Hej, robot!")
print(f"Poäng: {poäng}")   # f-string: sätt in variabler med {}
```

### Variabler
```python
x = 5
namn = "Robot"
är_hemma = True   # Boolean: True eller False
```

### If-satser (beslut)
```python
if smuts == True:
    print("Det finns smuts här!")
elif poäng > 0:
    print("Bra jobbat!")
else:
    print("Ingen smuts.")
```

### Loopar
```python
# Upprepa 5 gånger
for i in range(5):
    print(i)   # Skriver ut: 0, 1, 2, 3, 4

# Loopa igenom en lista
for cell in rutnät:
    print(cell)
```

### Listor
```python
min_lista = [1, 2, 3, 4]
min_lista.append(5)     # Lägg till element
min_lista.pop()         # Ta bort sista elementet
längd = len(min_lista)  # Antal element
```

### Funktioner
```python
def flytta_höger(x, y):
    return x + 1, y   # Returnera ny position

ny_x, ny_y = flytta_höger(3, 2)
```

### Klasser (avancerat)
```python
class Robot:
    def __init__(self):
        self.x = 1
        self.y = 1
    
    def flytta_höger(self):
        self.x += 1
```

---

## 📚 Resurser

| Resurs | Länk |
|--------|------|
| 🤖 Laborationen (Google Colab) | [Öppna Lab 1](https://colab.research.google.com/github/karye/Liu-labbar/blob/main/Lab_1_Cleaner_Robot_SE.ipynb) |
| 📖 Python dokumentation | [docs.python.org](https://docs.python.org/3/) |
| 🆘 Google Colab hjälp | [colab.research.google.com/notebooks/intro.ipynb](https://colab.research.google.com/notebooks/intro.ipynb) |

---

## 💪 Motiverande avslutning

> **Du är på väg att lära dig något som få människor kan.**

AI är framtiden – och du håller just nu på att förstå hur det faktiskt fungerar under huven. Det är inte magi, det är matematik och logik.

Det här är **svårt ibland** – och det är helt normalt. Varje programmerare fastnar. Varje AI-forskare har debuggat kod i timmar. Det hör till.

Men du KAN göra det. Ett steg i taget. En cell i taget.

**Lycka till! 🚀🤖✨**

---

*Baserad på originalversion av Mattias Tiger, LiU. Förenklad version CC BY-NC-SA 4.0.*
