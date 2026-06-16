# 🎮 Snabbguide för Tre i rad – AI-kurs

> **För dig som är ny på programmering – välkommen! Den här guiden hjälper dig hela vägen.**

---

## 👋 Välkommen!

Du ska nu lära dig programmera en AI som spelar Tre i rad! Det låter kanske svårt, men vi tar det steg för steg. Efter dessa 6 lektioner kommer du att ha skapat din egen AI-agent som kan spela spel – precis som de stora AI-systemen, fast lite enklare.

**Du behöver inte kunna programmering sedan tidigare.** Vi börjar från grunden.

---

## ❌⭕ Vad är Tre i rad?

Tre i rad (även kallat Tic-Tac-Toe) är ett spel för två spelare:

- En spelare använder **X**, den andra **O**
- Spelarna turas om att placera sin symbol på ett 3×3-bräde
- Den som först får **tre i rad** (vågrätt, lodrätt eller diagonalt) **vinner**
- Om brädet fylls utan att någon vinner blir det **oavgjort**

```
 0 | 1 | 2     ← kolumner
-----------
 3 | 4 | 5
-----------
 6 | 7 | 8

Eller som rad/kolumn:
       kol 0  kol 1  kol 2
rad 0 [  X  |  O  |  X  ]
rad 1 [  O  |  X  |     ]
rad 2 [     |  O  |  X  ]  ← X vinner diagonalt!
```

**Vinnande kombinationer:**
- Rad 0, 1 eller 2 (vågrätt)
- Kolumn 0, 1 eller 2 (lodrätt)
- Diagonal uppifrån-vänster till nerifrån-höger
- Diagonal uppifrån-höger till nerifrån-vänster

---

## 💻 Hur kör man en notebook?

Vi använder **Google Colab** – ett gratis verktyg i webbläsaren. Du behöver inget att installera!

### Steg 1: Öppna Google Colab
1. Gå till **colab.research.google.com**
2. Logga in med ditt Google-konto (eller skolkonto)
3. Klicka på **"Arkiv" → "Öppna notebook"**
4. Välj den fil läraren har delat med dig

### Steg 2: Förstå gränssnittet
```
┌─────────────────────────────────────────────┐
│  📄 Fil  ✏️ Redigera  📋 Infoga  ...         │  ← Menyrad
├─────────────────────────────────────────────┤
│  [▶ Kör]  Textruta med förklaringar          │  ← Textruta (grå bakgrund)
├─────────────────────────────────────────────┤
│  [▶ Kör]  # Python-kod här                  │  ← Kodruta (mörk bakgrund)
│           print("Hej!")                     │
├─────────────────────────────────────────────┤
│           Hej!                              │  ← Resultat visas här
└─────────────────────────────────────────────┘
```

### Steg 3: Kör kod
- **Klicka på ▶-knappen** till vänster om en kodruta, ELLER
- **Tryck Shift+Enter** när du står i en kodruta
- Resultatet visas direkt under kodrutan
- En **grön bock** ✅ = koden körde utan fel
- En **röd text** ❌ = det finns ett fel – läs felmeddelandet!

### Steg 4: Ändra och experimentera
- Klicka inuti en kodruta för att redigera
- Prova att ändra värden och se vad som händer
- Det är **omöjligt att förstöra** – du kan alltid starta om

### Steg 5: Om något går fel
- Klicka på **"Körmiljö" → "Starta om och kör alla"** för att börja om
- Kontrollera att du kört cellerna **uppifrån och ned** i ordning

---

## 📚 Ordbok – AI och programmering

### A

**Agent**
> En "spelare" i ett spel eller system som fattar beslut. I den här kursen är agenten ett program som väljer drag i Tre i rad.
> *Exempel: random_agent, smart_agent, minimax_agent*

**Algoritm**
> En steg-för-steg-instruktion för att lösa ett problem. Som ett recept, fast för datorer.
> *Exempel: "Kolla varje rad. Finns det tre likadana? Då är det vinnare."*

**Argument**
> Ett värde du skickar in i en funktion. Står inom parenteserna.
> *Exempel: `check_winner(board)` – här är `board` ett argument*

### B

**BFS (Bredden-först sökning)**
> *Breadth-First Search* – En sökalgoritm som utforskar alla möjligheter på en nivå innan den går djupare. Som att söka igenom en labyrint våning för våning.

**Boolean**
> Ett värde som antingen är `True` (sant) eller `False` (falskt).
> *Exempel: `har_vunnit = True`*

**Bräde / Spelplan**
> I koden representeras brädet som en lista med tre listor (en 2D-lista).
> ```python
> board = [
>     [" ", " ", " "],  # Rad 0
>     [" ", " ", " "],  # Rad 1
>     [" ", " ", " "]   # Rad 2
> ]
> ```

### D

**DFS (Djupet-först sökning)**
> *Depth-First Search* – En sökalgoritm som följer en väg så långt det går innan den backar. Som att utforska en labyrint en korridor i taget.

**Dictionary (dict)**
> En datastruktur med nyckel-värde-par. 
> *Exempel: `{"namn": "Anna", "ålder": 16}`*

**Djup (depth)**
> I sökträd: hur många drag framåt algoritmen tittar.

### F

**Funktion**
> Ett namngivet kodblock som utför en uppgift. Definieras med `def`.
> ```python
> def hälsa(namn):
>     print("Hej, " + namn + "!")
> 
> hälsa("Anna")  # Skriver ut: Hej, Anna!
> ```

**For-loop**
> Upprepar kod för varje element i en lista.
> ```python
> for rad in board:
>     print(rad)
> ```

### I

**Index**
> Positionen för ett element i en lista. Börjar alltid på **0**!
> ```python
> lista = ["a", "b", "c"]
>          #  0     1     2
> lista[0]  # → "a"
> lista[2]  # → "c"
> ```

**If-sats**
> Kör kod bara om ett villkor är sant.
> ```python
> if board[0][0] == "X":
>     print("X är i övre vänstra hörnet!")
> ```

### K

**Kö (Queue)**
> En datastruktur där det första som läggs in är det första som tas ut (FIFO). Används i BFS.

### L

**Lista**
> En samling värden i ordning.
> ```python
> tomma_rutor = [(0,1), (1,2), (2,0)]
> ```

### M

**Minimax**
> En algoritm för att hitta det bästa draget i ett spel. Den maximerar sin egen poäng och minimerar motståndarens. Ger "perfekt" spel i Tre i rad.

### R

**Rekursion**
> När en funktion anropar sig själv. Används i DFS och Minimax.
> ```python
> def räkna_ned(n):
>     if n == 0:
>         print("Klar!")
>     else:
>         print(n)
>         räkna_ned(n - 1)  # ← anropar sig själv!
> ```

**Return**
> Skickar tillbaka ett värde från en funktion.
> ```python
> def addera(a, b):
>     return a + b
> 
> resultat = addera(3, 4)  # resultat = 7
> ```

**Regelbaserad AI**
> En AI som följer handskrivna regler ("om X, gör Y"). Enklare än Minimax men kan göra misstag.

### S

**Slumpmässig agent**
> En AI som väljer drag helt slumpmässigt. Dålig spelare men enkel att koda!

**Stack**
> En datastruktur där det sista som läggs in är det första som tas ut (LIFO). Används i DFS.

**String (sträng)**
> Text i Python. Skrivs med citattecken.
> *Exempel: `"X"`, `"O"`, `" "` (tomt)*

### T

**Tuple**
> En oföränderlig lista. Skrivs med parenteser.
> *Exempel: `(rad, kolumn)` = `(1, 2)`*

---

## 🐍 Python-syntax snabbref

### Skapa ett tomt bräde
```python
board = [[" " for _ in range(3)] for _ in range(3)]
```

### Placera ett drag
```python
board[rad][kolumn] = "X"   # Placera X på rad 0, kolumn 2
board[0][2] = "X"
```

### Kolla om en ruta är tom
```python
if board[rad][kolumn] == " ":
    print("Rutan är tom!")
```

### Loopa igenom brädet
```python
for rad in range(3):
    for kolumn in range(3):
        print(board[rad][kolumn])
```

### Hitta tomma rutor
```python
tomma = []
for rad in range(3):
    for kolumn in range(3):
        if board[rad][kolumn] == " ":
            tomma.append((rad, kolumn))
```

### Importera slump
```python
import random
val = random.choice(tomma)  # Välj ett slumpmässigt element
```

### Kopiera en lista (viktigt!)
```python
import copy
ny_board = copy.deepcopy(board)  # Skapar en KOPIA, inte en referens
```

### Definiera en funktion
```python
def min_funktion(parameter1, parameter2):
    # kod här
    return resultat
```

### Vanliga jämförelseoperatorer
```python
==   # lika med
!=   # inte lika med
>    # större än
<    # mindre än
and  # och (båda måste vara sanna)
or   # eller (minst en måste vara sann)
not  # inte
```

---

## ❓ Vanliga frågor (FAQ)

**F: Jag får ett fel som säger "IndexError: list index out of range". Vad betyder det?**
> S: Du försöker nå ett index som inte finns. Kom ihåg att index börjar på 0 och slutar på 2 (inte 3!) i ett 3×3-bräde.
> Kontrollera att `rad` och `kolumn` är mellan 0 och 2.

**F: Varför skriver koden `board[rad][kolumn]` och inte `board[kolumn][rad]`?**
> S: Brädet är en lista av rader. `board[0]` är rad 0, och `board[0][1]` är kolumn 1 på rad 0. Tänk: rad först, kolumn sedan – precis som koordinater i matematik.

**F: Vad är skillnaden mellan `=` och `==`?**
> S: `=` tilldelar ett värde (`x = 5` ger x värdet 5). `==` jämför två värden (`x == 5` frågar "är x lika med 5?").

**F: Varför måste jag köra cellerna uppifrån och ned?**
> S: Varje cell kan använda funktioner och variabler från tidigare celler. Om du hoppar över en cell kanske Python inte känner till den funktion du försöker använda.

**F: Hur gör jag om jag vill testa mitt eget drag?**
> S: I Lektion 2 finns interaktiva knappar. I andra lektioner kan du skriva `board[rad][kolumn] = "X"` direkt i koden och sedan köra `visa_bräde(board)`.

**F: Min AI verkar alltid välja samma drag. Är det fel?**
> S: Om du använder `random_agent` ska det vara slumpmässigt – kör cellen igen för att se olika drag. Om du använder `smart_agent` eller `minimax_agent` är det normalt att de väljer samma "bästa" drag i samma situation.

**F: Vad betyder `None` i Python?**
> S: `None` representerar "ingenting" eller "inget värde". Det returneras t.ex. av `check_winner` när ingen har vunnit ännu.

**F: Jag förstår inte rekursion. Hur fungerar det?**
> S: Tänk på ryska dockor (matrjosjka) – varje docka innehåller en mindre docka, tills den är för liten för att öppnas. En rekursiv funktion anropar sig själv med ett mindre problem, tills problemet är tillräckligt litet för att lösas direkt (basfallet).

**F: Vad är skillnaden mellan DFS och BFS?**
> S: Tänk på en labyrint. DFS går in en korridor så långt det går, och backar sedan. BFS utforskar alla korridorer på samma avstånd samtidigt. BFS hittar alltid kortaste vägen; DFS är ofta snabbare att implementera.

**F: Är Minimax verkligen perfekt? Kan det förlora?**
> S: Nej! Minimax spelar perfekt Tre i rad och kan aldrig förlora. Det värsta som kan hända är oavgjort. Om du slår Minimax har du hittat ett fel i koden.

**F: Varför använder vi `copy.deepcopy(board)` i Minimax?**
> S: Om vi inte kopierar brädet och gör ett testdrag, förstör vi det riktiga brädet. `deepcopy` skapar en helt oberoende kopia som vi kan modifiera utan konsekvenser.

**F: Hur lång tid tar Minimax att köra?**
> S: För ett tomt 3×3-bräde tittar Minimax på upp till 9! = 362 880 möjliga spelordningar, men med Alpha-Beta-beskärning (avancerat) kan det optimeras kraftigt. Normalt sett är det nästan omedelbart.

---

## 🆘 Om du fastnar

### Steg 1: Läs felmeddelandet
Python berättar *vad* som gick fel och *var*. Läs det noggrant!
```
TypeError: unsupported operand type(s) for +: 'int' and 'str'
                                                ↑          ↑
                                            Du försöker addera ett tal och text
```

### Steg 2: Kolla variabelnamnen
Är stavningen rätt? Python är känsligt för stora/små bokstäver:
- `Board` ≠ `board`
- `Check_Winner` ≠ `check_winner`

### Steg 3: Lägg till print-satser
```python
print("Nu är jag här!")
print("board =", board)
print("rad =", rad, "kolumn =", kolumn)
```

### Steg 4: Starta om och kör alla celler igen
Klicka: **Körmiljö → Starta om och kör alla**

### Steg 5: Jämför med ett exempel
Titta på koden som redan är given i notebooken – din kod borde se ut på liknande sätt.

### Steg 6: Fråga en kompis
Förklara problemet högt för någon annan. Ofta hittar man felet medan man förklarar!

### Steg 7: Fråga läraren
Berätta:
1. Vad du försöker göra
2. Vad du trodde skulle hända
3. Vad som faktiskt hände (visa felmeddelandet)

---

## 💪 Du klarar det!

Programmering är en färdighet som tar tid att lära sig – precis som att lära sig ett nytt språk eller spela ett instrument. Det är **helt normalt** att göra misstag. Faktum är att professionella programmerare spenderar mer tid på att felsöka (hitta och rätta fel) än att skriva ny kod!

**Kom ihåg:**
- ✅ Alla fel är läromöjligheter
- ✅ Det finns inga dumma frågor
- ✅ Experimentera gärna – du kan inte förstöra något
- ✅ Varje lektion bygger på den förra – ta det i din takt

**Du skapar bokstavligen en AI. Det är coolt! 🤖**

---

*Lycka till med kursen! /Lärarlaget*
