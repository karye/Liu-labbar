# 📚 Lärarguide – Lab 1: Städrobot

> **Detaljerad guide för lärare som genomför laborationen "Städrobot – AI-agenter i ett rutnät"**

---

## 📋 Innehållsförteckning

1. [Om kursen](#om-kursen)
2. [Tekniska förberedelser](#tekniska-förberedelser)
3. [Lab 1.0 – Rutnätsvärlden](#lab-10--rutnätsvärlden)
4. [Lab 1.1 – Simulering och manuell styrning](#lab-11--simulering-och-manuell-styrning)
5. [Lab 1.2 – Lös problemet i känd miljö](#lab-12--lös-problemet-i-känd-miljö)
6. [Lab 1.3 – Byt till okänd miljö](#lab-13--byt-till-okänd-miljö)
7. [Lab 1.4 – Lös problemet i okänd miljö](#lab-14--lös-problemet-i-okänd-miljö)
8. [Svar på alla quiz-frågor](#svar-på-alla-quiz-frågor)
9. [Vanliga problem och lösningar](#vanliga-problem-och-lösningar)
10. [Differentieringsmöjligheter](#differentieringsmöjligheter)
11. [Övergripande tips](#övergripande-tips)

---

## Om kursen

### Vad är denna kurs?

Laborationen introducerar elever till **AI-agenter** genom simuleringen av en städrobot som navigerar i ett rutnät. Eleverna börjar med att utforska miljön, styr roboten manuellt, och avslutar med att förstå sökalgoritmer (BFS och DFT).

Kursen är baserad på originalversion av **Mattias Tiger, mattias.tiger@liu.se**, förenklad för nybörjare på svenska.

### Målgrupp

- **Ålder:** 15–17 år (gymnasieelever)
- **Förkunskaper:** Liten eller ingen programmeringserfarenhet krävs
- Python-syntax introduceras gradvis med massor av kommentarer

### Tidsåtgång

| Del | Namn | Tid (ca) |
|-----|------|----------|
| Lab 1.0 | Rutnätsvärlden | 30–40 min |
| Lab 1.1 | Simulering och manuell styrning | 30–40 min |
| Lab 1.2 | Känd miljö – BFS-planering | 40–60 min |
| Lab 1.3 | Okänd miljö – manuell utforskning | 20–30 min |
| Lab 1.4 | Okänd miljö – BFS-planering | 30–40 min |
| **Totalt** | | **~3–4 timmar** |

### Vad eleverna lär sig

- Vad en **AI-agent** är och hur den interagerar med sin miljö
- Hur man representerar en värld i ett **rutnät**
- Skillnaden mellan **känd** och **okänd miljö**
- Vad **perception** och **åtgärder** är i AI-sammanhang
- Hur **BFS** (bredden-först-sökning) fungerar
- Hur **DFT** (djupet-först-traversering) fungerar
- Grundläggande Python (klasser, funktioner, listor, if-satser)

### Licens

CC BY-NC-SA 4.0 – Laborationen är fri att använda, dela och modifiera.

---

## Tekniska förberedelser

### Vad du behöver

- Eleverna behöver **Google-konton** (för Google Colab)
- **Internetanslutning** (Colab kräver internet)
- En webbläsare (Chrome rekommenderas för bästa Colab-upplevelse)

### Innan lektionen

1. **Testa notebooken** – kör igenom hela laborationen själv minst en gång
2. **Öppna länken i förväg:** [Lab 1 på Colab](https://colab.research.google.com/github/karye/Liu-labbar/blob/main/Lab_1_Cleaner_Robot_SE.ipynb)
3. **Kontrollera att Colab fungerar** i klassrummet (nätverksbegränsningar?)
4. Förbered en projicering för att visa koden för hela klassen

### Hur eleverna öppnar laborationen

1. Gå till GitHub-länken i notebooken (Colab-badge i toppen)
2. Eller navigera direkt till: `colab.research.google.com`
3. Välj "GitHub" och klistra in: `karye/Liu-labbar`
4. Välj `Lab_1_Cleaner_Robot_SE.ipynb`

### Viktigt om Colab

- Eleverna måste **spara en kopia** i sin egen Google Drive (`Arkiv → Spara en kopia på Drive`)
- Annars förlorar de sitt arbete när sessionen stängs!
- Påminn eleverna om detta i **börjat av varje lektion**

---

## Lab 1.0 – Rutnätsvärlden

### Pedagogiska mål

- Förstå hur en AI-miljö kan representeras som ett rutnät
- Lära sig om celltyper (tom, vägg, smuts, hem)
- Förstå koordinatsystemet (x, y)

### Före lektionen

**Förbered svar på:**
- Hur många celltyper finns det? (5: tom, vägg, smuts, hem, okänd)
- Hur ser koordinatsystemet ut? (x ökar höger, y ökar nedåt)
- Vad händer om man ändrar `wall_density`?

**Vanliga misstag elever gör:**
- Förväxlar x och y (kom ihåg: x = horisontellt, y = vertikalt)
- Ändrar koden men glömmer att köra om cellen
- Kör celler i fel ordning (kör alltid uppifrån!)

### Under lektionen

**Steg-för-steg (ca 35 min):**

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Introduktion: "Vad är en städrobot? Var har ni sett robotar som städar?" |
| 5–10 min | Visa rutnätskonceptet på tavlan med ASCII-art |
| 10–20 min | Elever kör Cell 3–4 (imports och CellType) |
| 20–30 min | Elever kör Cell 6 (generera scenario) och svarar på Fråga 2–4 |
| 30–35 min | Elever kör Cell 8 (koordinatvisning) och svarar på Fråga 5 |

**Vad eleverna ska ha gjort:**
- ✅ Kört alla kodceller i Lab 1.0
- ✅ Svarat på Fråga 1–5
- ✅ Sett ett rutnät visualiseras

**Checkpoint-frågor:**
- "Hur många typer av celler finns det?" → 5 typer
- "Vad representerar `░` symbolerna?" → Smuts
- "Var börjar roboten?" → Position (1,1) – övre vänstra hörnet

### Svar på quiz-frågor (Lab 1.0)

**Uppgift 1.0.1 – Fråga 1:** *Hur många celltyper finns det?*
> **Svar: 5 stycken** – Tom (0), Vägg (1), Smuts (2), Hem (3), Okänd (4)
>
> *Eleverna hittar svaret i `class CellType` i koden.*

**Uppgift 1.0.3 – Fråga 2:** *Hur stor är rutnätsvärlden?*
> **Svar: 10 × 10** – Definieras av `grid_size = 10`
>
> *Eleverna kan räkna symbolerna i utskriften.*

**Uppgift 1.0.3 – Fråga 3:** *Vad händer om du ändrar wall_density?*
> **Svar: Fler/färre väggar** – Värdet 0.0 = inga väggar, 1.0 = allt är väggar
>
> *Vanliga svar: "Det blir fler #" – acceptabelt!*

**Uppgift 1.0.3 – Fråga 4:** *Vad händer om du ändrar dirt_density?*
> **Svar: Mer/mindre smuts (░)** – Fungerar på samma sätt som wall_density

**Uppgift 1.0.4 – Fråga 5:** *Hur ändras y nedåt? Är det som förväntat?*
> **Svar: y ökar nedåt** – Det är bakvänt jämfört med matematik (y ökar uppåt) men normalt för skärmar
>
> *Förklara: Skärmar räknar pixlar uppifrån-och-ned – det är en gammal konvention.*

### Härtill hörande kodexempel

```python
# Exempel: Se alla celltyper
class CellType:
    EMPTY   = 0  # . (tom)
    WALL    = 1  # # (vägg)
    DIRT    = 2  # ░ (smuts)
    HOME    = 3  # H (hem)
    UNKNOWN = 4  # ? (okänd)

# Exempel: Generera en värld
grid_size    = 5   # Liten 5×5 värld
wall_density = 0.2 # 20% väggar
dirt_density = 0.2 # 20% smuts
grid, robot_pos = generate_scenario(grid_size, wall_density, dirt_density, False)
```

---

## Lab 1.1 – Simulering och manuell styrning

### Pedagogiska mål

- Förstå hur en **simulering** fungerar
- Lära sig om **åtgärder** (actions) och **poängsystemet**
- Uppleva skillnaden mellan att styra roboten manuellt och automatiskt

### Före lektionen

**Förbered svar på:**
- Vad är startpoängen? (-1000)
- Vilka 6 åtgärder finns det?
- Hur beräknas poängen?

**Vanliga misstag:**
- Elever försöker lösa problemet med väldigt låg poäng (negativt) – betona att det är OK i Lab 1.1
- Elever glömmer att återvända hem för att slutföra uppdraget

### Under lektionen

**Steg-för-steg (ca 35 min):**

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Repetition: "Vad lärde vi oss förra gången?" |
| 5–10 min | Introduktion till simulering och poängsystem |
| 10–15 min | Elever kör Cell 10 (agentåtgärder och miljö) och läser koden |
| 15–25 min | Elever kör Cell 12 (simuleringsgränssnittet) och styr roboten manuellt |
| 25–35 min | Elever löser tre probleminstanser och antecknar poäng |

**Vad eleverna ska ha gjort:**
- ✅ Förstår de 6 åtgärderna
- ✅ Löst minst 3 probleminstanser manuellt
- ✅ Svarat på Fråga 1–4
- ✅ Förstår poängsystemet

**Checkpoint-frågor:**
- "Vilka åtgärder kan roboten göra?" → 6 st: NOOP, UPP, NER, VÄNSTER, HÖGER, DAMMSUG
- "Vad är startpoängen?" → -1000
- "Vad händer med poängen när roboten rör sig?" → -1 per rörelse

### Svar på quiz-frågor (Lab 1.1)

**Uppgift 1.1.1 – Fråga 1:** *Vilka åtgärder kan städroboten utföra?*
> **Svar: 6 åtgärder:**
> - NOOP (Göra ingenting)
> - MOVE_UP (Röra sig uppåt)
> - MOVE_DOWN (Röra sig nedåt)
> - MOVE_LEFT (Röra sig vänster)
> - MOVE_RIGHT (Röra sig höger)
> - SUCK_DIRT (Dammsuga smuts)

**Uppgift 1.1.2 – Fråga 2:** *Vad är startpoängen?*
> **Svar: -1000**
>
> *Förklaring: Startpoängen är -1000 för att ta hänsyn till att roboten inte har städat ännu. Poängen ökar för varje smuts som städas (+100 per smuts) och minskar för varje åtgärd (-1 per åtgärd).*

**Uppgift 1.1.2 – Fråga 3:** *Vad händer med poängen?*
> **Svar:**
> - Varje rörelse: **-1 poäng**
> - Lyckad dammsugning (på smuts): **+100 poäng**
> - Misslyckad dammsugning (ingen smuts): **-1 poäng**

**Uppgift 1.1.3 – Fråga 4:** *Vilken poäng fick du för de tre körningarna?*
> **Svar: Varierar!** Acceptera alla rimliga svar (positiva eller negativa).
>
> *Bra poäng: ca -600 till -800 (kan variera mycket beroende på världen)*
>
> *Beräkning: -1000 + (antal smuts × 100) - (antal åtgärder)*

### Härtill hörande kodexempel

```python
# Poängberäkning
startpoäng = -1000
poäng_per_rörelse = -1
poäng_per_dammsugning = +100

# Exempelberäkning för 3 smutsar, 25 rörelser:
poäng = -1000 + (3 * 100) + (25 * -1)
# = -1000 + 300 - 25 = -725
```

---

## Lab 1.2 – Lös problemet i känd miljö

### Pedagogiska mål

- Förstå **djupet-först-traversering (DFT)**
- Förstå **bredden-först-sökning (BFS)**
- Se hur en AI-agent kan planera autonomt

### Före lektionen

**Det här är den svåraste delen!** Planera extra tid och ha tålamod.

**Förbered svar på:**
- Vad är DFT och hur fungerar det?
- Vad är BFS och hur fungerar det?
- Vad är skillnaden?

**Vanliga misstag:**
- Elever förstår inte skillnaden mellan DFT och BFS
- Elever förstår inte vad `frontier` och `visited` gör
- `lambda`-funktioner kan vara förvirrande

**Tips:** Rita ett enkelt rutnät på tavlan och visa DFT vs BFS för hand!

### Under lektionen

**Steg-för-steg (ca 50 min):**

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Introduktion: "Vad händer om roboten vet var all smuts finns?" |
| 5–15 min | Förklara DFT på tavlan med enkelt exempel |
| 15–25 min | Elever kör Cell 14–16 (DFT-kod) och svarar på frågor |
| 25–35 min | Förklara BFS på tavlan |
| 35–45 min | Elever kör Cell 18–22 (BFS-sökning) |
| 45–50 min | Elever kör Cell 25–27 (BFS-agent) och observerar resultaten |

**Vad eleverna ska ha gjort:**
- ✅ Kört DFT och sett sökvägen
- ✅ Kört BFS och sett den kortaste vägen
- ✅ Sett BFS-agenten lösa problemet automatiskt
- ✅ Svarat på alla frågor

**Checkpoint-frågor:**
- "Vad är skillnaden mellan DFT och BFS?" → DFT: djupet-först; BFS: bredden-först
- "Vilken algoritm ger kortaste vägen?" → BFS
- "Vilken algoritm besöker alla noder?" → DFT

### Svar på quiz-frågor (Lab 1.2)

**Uppgift 1.2.1 – Fråga 1:** *Hur många grannceller kan en cell ha maximalt?*
> **Svar: 4** – Upp, ner, vänster, höger (inte diagonalt)

**Uppgift 1.2.4 – Fråga 1:** *Täcker DFT-sökvägen alla nåbara positioner?*
> **Svar: Ja** – DFT besöker alla nåbara noder från startnoden

**Uppgift 1.2.4 – Fråga 2:** *Var slutar DFT-sökvägen?*
> **Svar: Beror på slumpen/världen** – t.ex. (3,1) i ett specifikt test
>
> *Förklaring: Slutpositionen för DFT är icke-deterministisk – den beror på grannarnas ordning.*

**Uppgift 1.2.4 – Fråga 3:** *Kan roboten följa sökvägen med sina åtgärder?*
> **Svar: Ja** – Men den behöver extra åtgärder för att hoppa mellan icke-angränsande positioner i stigen

**Uppgift 1.2.5 – Fråga 1:** *Kan roboten följa stigen nu med hjälp av sin plan?*
> **Svar: Ja** – BFS fyller i de saknade rörelserna mellan DFT-noderna

**Uppgift 1.2.5 – Fråga 2:** *Hur mycket längre är planen jämfört med stigen?*
> **Svar: Planen är längre** – DFT-stigen är en lista av koordinater; planen innehåller varje enskilt steg
>
> *Exempel: DFT-stig: 15 koordinater → Plan: kanske 30–40 åtgärder*

**Uppgift 1.2.7 – Fråga 1:** *Var hamnar du om du följer planen?*
> **Svar: På den närmaste smutspositionen**

**Uppgift 1.2.7 – Fråga 2:** *Vad är den kortaste planen till nästa smuts?*
> **Svar: Beror på positionen** – t.ex. UPP, HÖGER, UPP (varierar)

**Uppgift 1.2.9 – Fråga 1:** *Är det lätt eller svårt för den slumpmässiga agenten?*
> **Svar: Mycket svårt** – Den slumpmässiga agenten väljer slumpmässiga åtgärder och hittar inte smutsen effektivt
>
> *Typiskt: Den slumpmässiga agenten kan ta hundratals steg utan att lösa problemet*

**Uppgift 1.2.9 – Fråga 2:** *Vad gör BFS-agenten mer intelligent?*
> **Svar:** BFS-agenten vet var smutsen finns (känd miljö) och planerar **kortaste vägen** direkt till varje smutscell. Den städar systematiskt all smuts och återvänder hem.

### Härtill hörande kodexempel

```python
# DFT - Djupet-först-traversering (besöker alla nåbara noder)
def dft(start_node, map):
    visited  = []
    frontier = [start_node]   # Stack (LIFO: sist in, först ut)
    path = []
    
    while frontier:
        node = frontier.pop(-1)   # Pop från slutet = stack-beteende
        if node not in visited:
            path.append(node)
            visited.append(node)
            for neighbor in get_neighbors(node, map):
                frontier.append(neighbor)
    
    return path

# BFS - Bredden-först-sökning (hittar kortaste vägen)
def bfs(start_state, world, goal_condition):
    visited  = []
    frontier = [(start_state, [])]   # Kö (FIFO: först in, först ut)
    
    while frontier:
        state, plan = frontier.pop(0)   # Pop från början = kö-beteende
        
        if goal_condition(state, world):
            return plan   # Hittat! Returnera planen
        
        if state not in visited:
            visited.append(state)
            for action in AGENT_MOVE_ACTIONS:
                # Testa att flytta i varje riktning...
                # (förenkling av den faktiska koden)
                pass
    
    return []   # Ingen väg hittades
```

**Skillnaden mellan DFT och BFS:**

```
Rutnät:      DFT-ordning:      BFS-ordning (från S):
S . .        S → 1 → 2         S → 1 → 3 → 5
. . .        ↓         ↓       ↓   ↓   ↓   ↓
. . .        3 → 4 → 5 → 6     2 → 4 → 6 → 7

DFT: Gå så djupt som möjligt   BFS: Utforska lager för lager
     (bra för att besöka allt)       (bra för kortaste vägen)
```

---

## Lab 1.3 – Byt till okänd miljö

### Pedagogiska mål

- Förstå skillnaden mellan **känd** och **okänd** miljö
- Inse begränsningarna med att inte se hela världen
- Förstå varför utforskning krävs

### Under lektionen

**Steg-för-steg (ca 25 min):**

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Diskussion: "Tänk dig att du ska städa ett mörkt rum. Vad gör du?" |
| 5–15 min | Elever kör Cell 30 och styr roboten manuellt i okänd miljö |
| 15–25 min | Diskussion om strategier: "Hur utforskar man systematiskt?" |

### Svar på quiz-frågor (Lab 1.3)

**Uppgift 1.3.1 – Fråga 1:** *Är det här problemet svårare?*
> **Svar: Ja** – Roboten kan inte planera BFS direkt till smutsen eftersom den inte vet var smutsen är

**Uppgift 1.3.1 – Fråga 2:** *Kan vi använda vår tidigare BFS-lösning?*
> **Svar: Nej** – BFS söker efter smuts i känd karta. I okänd miljö är cellerna märkta som UNKNOWN (?)

**Uppgift 1.3.1 – Fråga 3:** *Vad är en bra alternativ strategi?*
> **Svar: Systematisk utforskning** – Besök alla okända celler systematiskt, precis som DFT men nu i realtid

---

## Lab 1.4 – Lös problemet i okänd miljö

### Pedagogiska mål

- Se hur BFS kan **anpassas** för okänd miljö
- Förstå begreppet **frontier-baserad utforskning**
- Jämföra slumpmässig agent vs. intelligent agent i okänd miljö

### Under lektionen

**Steg-för-steg (ca 35 min):**

| Tid | Aktivitet |
|-----|-----------|
| 0–5 min | Repetition: "Varför fungerar inte vår gamla BFS-agent i okänd miljö?" |
| 5–10 min | Förklara den nya strategin: BFS söker efter UNKNOWN celler |
| 10–20 min | Elever kör Cell 32–33 och observerar agenten |
| 20–30 min | Elever jämför slumpmässig agent vs. BFS-agent |
| 30–35 min | Diskussion: "Vad mer kan man göra för att förbättra agenten?" |

**Vad eleverna ska ha gjort:**
- ✅ Kört BFS-agenten i okänd miljö
- ✅ Jämfört med slumpmässig agent
- ✅ Svarat på alla frågor

### Svar på quiz-frågor (Lab 1.4)

**Uppgift 1.4.1 – Fråga 1:** *Är det lätt eller svårt för den slumpmässiga agenten?*
> **Svar: Svårt** – Samma problem som i känd miljö, men nu vet agenten inte ens var väggarna är

**Uppgift 1.4.1 – Fråga 2:** *Vad gör BFS-planeringsagenten mer intelligent?*
> **Svar:** Agenten söker systematiskt efter **okända celler** (UNKNOWN). Den besöker varje okänd cell i ordning, lär sig om världen gradvis, städar smuts när den hittar det, och returnerar hem när allt är utforskat.

---

## Svar på alla quiz-frågor

### Snabbregistret

| Del | Fråga | Svar (kortversion) |
|-----|-------|--------------------|
| 1.0.1 | Hur många celltyper? | 5 |
| 1.0.3 | Hur stor är världen? | 10×10 |
| 1.0.3 | Vad händer med wall_density? | Fler/färre väggar |
| 1.0.3 | Vad händer med dirt_density? | Mer/mindre smuts |
| 1.0.4 | Hur ändras y nedåt? | Ökar nedåt (skärmkonvention) |
| 1.1.1 | Vilka åtgärder kan roboten göra? | 6 st (NOOP, upp, ner, vänster, höger, dammsug) |
| 1.1.2 | Vad är startpoängen? | -1000 |
| 1.1.2 | Vad händer med poängen? | -1 per rörelse, +100 per dammsugning |
| 1.2.1 | Max antal grannar? | 4 |
| 1.2.4 | Täcker DFT alla nåbara positioner? | Ja |
| 1.2.4 | Kan roboten följa DFT-stigen? | Ja (med BFS som hjälp) |
| 1.2.9 | Är slumpmässig agent bra? | Nej, mycket ineffektiv |
| 1.2.9 | Vad gör BFS-agent bättre? | Planerar kortaste väg till varje smuts |
| 1.3.1 | Är okänd miljö svårare? | Ja |
| 1.3.1 | Kan vi använda gamla BFS? | Nej |
| 1.3.1 | Bra strategi i okänd miljö? | Systematisk utforskning |
| 1.4.1 | Vad gör BFS bättre i okänd miljö? | Söker UNKNOWN-celler systematiskt |

---

## Vanliga problem och lösningar

### "Elevens kod körs inte"

**Symptom:** Ingenting händer när eleven trycker Shift+Enter

**Lösningar:**
1. Kontrollera att cellen är markerad (blå kant)
2. Klicka på cellen och försök igen
3. Kontrollera internetanslutningen (Colab kräver internet)
4. Kontrollera om det finns ett `*` bredvid cellen (väntar på runtime)
5. Kör `Runtime → Restart runtime` och börja om

### "Elevens visualisering är tom / syns inte"

**Symptom:** Ingen rutnätsutskrift visas

**Lösningar:**
1. Eleven har inte kört **cell 3 och 4** (importcellerna) – kör dem först
2. Eleven har kört cellerna i fel ordning – starta om från toppen
3. `widgets.Output()` kan ibland kräva att man kör cellen två gånger

### "Agenten fastnar i en loop"

**Symptom:** Agenten verkar gå i cirklar och kommer aldrig hem

**Lösningar:**
1. Klicka på `Återställ` knappen i gränssnittet
2. Kör om kodcellen för en ny probleminstans
3. Om det är BFS-agenten: kontrollera att `visited`-listan fungerar korrekt

### "Runtime disconnected / session har gått ut"

**Symptom:** Colab tappar anslutning

**Lösning:** 
1. Återanslut (klicka "Reconnect" i Colab)
2. Kör **alla** celler uppifrån igen (Runtime → Run all)

### "ModuleNotFoundError: No module named 'ipywidgets'"

**Symptom:** Felmeddelande om ipywidgets

**Lösning:** Kör `!pip install ipywidgets` i en cell och starta om runtime

### "IndexError / KeyError vid rutnätsoperationer"

**Symptom:** Fel när roboten rör sig utanför rutnätet

**Lösning:** Detta är en bug – eleverna har förändrat koordinatberäkningarna. Kolla `get_neighbors()`-funktionen.

---

## Differentieringsmöjligheter

### För snabba elever (om de är klara tidigt)

**Lab 1.0 extra:**
- Ändra rutnätsstorleken till 20×20 eller 5×5 – vad händer?
- Skapa en värld utan väggar – vad händer med antalet möjliga vägar?

**Lab 1.1 extra:**
- Försök lösa problemet med **så få åtgärder som möjligt** – vad är minimumet?
- Testa `random_home = True` – hur påverkar det svårigheten?

**Lab 1.2 extra:**
- Kan du modifiera BFS för att städa smuts i en **specifik ordning** (t.ex. närmast hem sist)?
- Kan du skapa en agent som **kombinerar** DFT och BFS?
- Skriv en egen agent-klass från grunden

**Lab 1.4 extra:**
- Kan du skapa en agent som **minns** var smuts brukar finnas?
- Utforska: Vad händer om roboten inte vet var den startade?

### För långsamma elever (om de behöver mer stöd)

- Hoppa över att läsa all kod – fokusera bara på att **köra cellerna** och svara på frågorna
- Para ihop eleverna (en starkare + en svagare)
- Ge "cheat sheet" med de viktigaste begreppen (se Snabbguide för elever)
- Tillåt att de hoppar Lab 1.2 detaljerna och bara ser resultaten

---

## Övergripande tips

### Classroom management

- **Börja alltid med en demonstration** – visa på projicering hur man kör en cell
- **Påminn eleverna om att spara** – De förlorar arbete om de inte sparar till Drive
- **Gå runt** – Kontrollera att eleverna inte sitter fast länge utan att fråga
- **Pausa klassen** vid viktiga punkter – Säg "Nu ska alla ha kommit hit. Räck upp handen om du inte är klar"

### Hur man håller eleverna engagerade

- Ställ **retoriska frågor**: "Varför tror ni att en robot behöver veta om det finns en vägg?"
- Koppla till **vardagen**: "Tänk på din Roomba hemma – hur tror du den navigerar?"
- Låt elever **tävla**: "Vem kan lösa problemet med högst poäng?"
- Fira **framsteg**: "Nu har ni faktiskt skrivit kod som löser ett AI-problem!"

### Kognitiva milstolpar (vad är svårt att förstå)

1. **Koordinatsystemet** (x,y med y nedåt) – Visa med konkret exempel
2. **Skillnaden DFT vs BFS** – Rita på tavlan
3. **Vad `lambda` gör** – Förklara som "en liten namnlös funktion"
4. **Känd vs okänd miljö** – Koppla till mörkt rum-analogin

### Grupparbete vs individuellt arbete

- **Lab 1.0 och 1.1:** Kan göras i par (en kör, en läser)
- **Lab 1.2:** Rekommenderas individuellt (varje elev bör förstå BFS)
- **Lab 1.3 och 1.4:** Kan diskuteras i grupp

### Hemuppgifter (valfritt)

1. "Hitta ett exempel på en riktig städrobot (t.ex. Roomba) och förklara hur den navigerar"
2. "Rita ett rutnät på papper och visa hur BFS hittar kortaste vägen"
3. "Skriv en pseudokod för en agent som städar från vänster till höger, rad för rad"

---

*Baserad på originalversion av Mattias Tiger, LiU. Förenklad version CC BY-NC-SA 4.0.*
