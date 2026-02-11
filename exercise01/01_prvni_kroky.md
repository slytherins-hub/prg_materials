# CVIČENÍ 1: PRVNÍ KROKY S PYTHONEM

Algoritmizace a programování

## ÚVOD

Vítejte v kurzu programování! Možná si říkáte: "Proč bych se měl učit programovat, když existují AI nástroje?" nebo "Já budu v medicíně, k čemu mi to bude?" Odpověď je jednoduchá: **umět programovat znamená umět řešit problémy systematicky** – a to je dovednost, kterou využijete všude.

### Proč umět programovat?

#### Programování v medicíně a bioinženýrství

Pokud chcete dělat zajímavou a perspektivní práci, programování je klíčové:

**Lékařská diagnostika a analýza:**
- Detekce nádorů a tkání v CT či MR obrazech
- Umělá inteligence pro diagnostiku onemocnění
- Biometrie a zpracování biologických signálů
- Algoritmy pro laboratorní, diagnostické a terapeutické přístroje

**Mobilní a nositelné technologie:**
- Aplikace pro zdravotnickou záchrannou službu
- Sport technology a fitness trackery
- Wearable devices (chytré hodinky, senzory)
- Monitorování pacientů na dálku

**A kam se programování ještě vejde?**

Podívejte se na svůj rozvrh – **programování se v něm objeví znovu a znovu**:

| 1. ročník                        | 2. ročník                             | 3. ročník                               |
|----------------------------------|---------------------------------------|-----------------------------------------|
| **Algoritmizace a programování** | Úvod do medicínské informatiky        | Umělá inteligence v medicíně            |
|                                  | Číslicové zpracování signálů a obrazů | Modely v biologii a epidemiologii       |
|                                  | Bioinformatika                        | Praktika z bioinformatiky               |
|                                  | Analýza biologických signálů          | Semestrální práce, **Bakalářská práce** |

> **Vyhnout se programování nejde.** Buď se ho naučíte teď pořádně, nebo budete trpět později.

### Co je to algoritmus?

Než začneme psát kód, musíme pochopit, co vlastně programujeme. **Algoritmus** je **přesně definovaný postup**, jak dojít od vstupu k výstupu.

**Příklad z běžného života:**
```
Vstup: Ingredience (mouka, vejce, mléko)
Algoritmus: Recept na palačinky (smíchej, ohřej pánev, smaž...)
Výstup: Hotové palačinky
```

#### Základní požadavky na algoritmus

Dobrý algoritmus musí splňovat 5 vlastností:

| Vlastnost          | Význam                               | Příklad (špatně → dobře)                              |
|--------------------|--------------------------------------|-------------------------------------------------------|
| **Vstup a výstup** | 0 nebo více vstupů, alespoň 1 výstup | "Udělej něco" → "Sečti čísla a vrať výsledek"         |
| **Efektivita**     | Minimální nároky na paměť a čas      | Hledání v seznamu: projít vše vs. binární vyhledávání |
| **Jednoznačnost**  | Každý krok přesně definován          | "Ohřej trochu" → "Ohřej na 180 °C"                    |
| **Univerzálnost**  | Řeší celou třídu problémů            | "Sečti 5+3" → "Sečti dvě čísla"                       |
| **Konečnost**      | Musí skončit po konečném počtu kroků | "Opakuj, dokud..." → "Opakuj 5×"                      |

**Příklad špatného algoritmu:**
```
1. Vezmi dva kousíčky
2. Smíchej je trochu
3. Opakuj, dokud to nebude dobré
```
Proč je špatný? Není jednoznačný ("kousíčky" = kolik?), není jasná konečnost ("dokud to nebude dobré" = kdy?).

**Dobrý algoritmus:**
```python
1. Načti dvě čísla: a, b
2. Sečti je: vysledek = a + b
3. Vrať vysledek
```
Splňuje vše: jasný vstup (a, b), jednoznačné kroky, skončí po 3 krocích, funguje pro libovolná čísla.

**Praktický příklad z medicíny:** Algoritmus pro detekci horečky

```python
# Špatně - nejasné
"Pokud má pacient teplotu, zavolej doktora"

# Dobře - přesné
1. Načti teplotu pacienta (°C)
2. Je teplota >= 38.0?
   ANO: Zašli upozornění lékaři
   NE: Pokračuj v monitorování
3. Zapiš měření do databáze
```

Tento algoritmus má jasný vstup (teplota), jednoznačné kroky (konkrétní hodnota 38.0 °C), vždy skončí a funguje univerzálně pro všechny pacienty.

### Proč Python?

Existují desítky programovacích jazyků (C, Java, JavaScript, R...). Proč zrovna Python?

#### 1. Jednoduchá syntaxe
Python vypadá skoro jako angličtina. Porovnejte **stejný program** v různých jazycích:

**Python:**
```python
temperatures = [36.5, 37.2, 38.1, 37.8]
average = sum(temperatures) / len(temperatures)
print(f"Průměrná teplota: {average} °C")
```

**Java:**
```java
double[] temperatures = {36.5, 37.2, 38.1, 37.8};
double sum = 0;
for (double temp : temperatures) {
    sum += temp;
}
double average = sum / temperatures.length;
System.out.printf("Průměrná teplota: %.1f °C\n", average);
```

**C:**
```c
#include <stdio.h>
int main() {
    double temps[] = {36.5, 37.2, 38.1, 37.8};
    double sum = 0;
    int n = sizeof(temps) / sizeof(temps[0]);
    for (int i = 0; i < n; i++) {
        sum += temps[i];
    }
    printf("Průměrná teplota: %.1f °C\n", sum / n);
    return 0;
}
```

**JavaScript:**
```javascript
const temperatures = [36.5, 37.2, 38.1, 37.8];
const average = temperatures.reduce((a, b) => a + b) / temperatures.length;
console.log(`Průměrná teplota: ${average.toFixed(1)} °C`);
```

Všimněte si: Python má **3 řádky**, Java 7, C 10. Python je nejčitelnější.

#### 2. Nejpoužívanější jazyk
Podle žebříčků TIOBE (2024–2026) je Python nejpoužívanější jazyk světa. Na GitHubu je 2. nejčastější.

**Stručná historie Pythonu:**

```
1991 ━━ Guido van Rossum vydává Python 0.9.0
       "Monty Python" → název jazyka 🐍
       
2000 ━━ Python 2.0 (list comprehensions, Unicode)
       
2008 ━━ Python 3.0 (zlom kompatibility)
       
2015 ━━ Boom v datové vědě (Pandas, NumPy)
       
2018 ━━ AI revoluce (TensorFlow, PyTorch mainstream)
       
2024 ━━ Python #1 na TIOBE
       Většina AI modelů běží na Pythonu
```

**Kdo používá Python?**
- **Google** – vyhledávání, YouTube, Gmail
- **Meta** – Instagram (Django framework)
- **Netflix** – doporučovací systémy
- **Spotify** – analýza dat, doporučení hudby
- **NASA** – analýza dat z vesmíru
- **CERN** – analýza dat z urychlovače částic

#### 3. Flexibilita
Python umí **všechno**:
- **Vědecké výpočty** (NumPy, SciPy)
- **Datová analytika** (Pandas, Matplotlib)
- **Umělá inteligence** (TensorFlow, PyTorch)
- **Webové aplikace** (Django, Flask)
- **Automatizace** (skripty pro úkoly)

#### 4. Obrovská komunita
- **Stack Overflow** – 5. největší komunita (miliony odpovědí)
- **GitHub** – statisíce open-source projektů
- Pokud máte problém, někdo už ho vyřešil a odpověď je na Google

### Role AI nástrojů (GitHub Copilot)

Programování se mění a nástroje jako **GitHub Copilot** se stávají průmyslovým standardem. Je **velmi důležité**, abyste se s nimi v budoucnu naučili pracovat.

> **⚠️ Důležité pro začátečníky:**
> I když jsou AI asistenti skvělí, **první kroky musíte zvládnout sami**. Pokud si základy (proměnné, cykly, podmínky) "neodřete" vlastním psaním a chybováním, nenaučíte se algoritmicky myslet. Bez pevných základů navíc nedokážete poznat, kdy AI udělala chybu – a to se stává častěji, než si myslíte. **Berte AI jako kalkulačku: je skvělá, ale musíte vědět, co počítáte.**

### Jak se naučit programovat?

**Programování se naučíte jedině programováním.** Je to dovednost jako sport nebo hra na hudební nástroj. Můžete přečíst stohy knih a zhlédnout hodiny videí, ale dokud nezačnete sami psát kód, dělat chyby a opravovat je, neposunete se. Žádná zkratka neexistuje, chce to jen čas a trpělivost.

**Kam se obrátit, když nevíte rady?**

| Zdroj              | Kdy/jak použít                           |
|--------------------|------------------------------------------|
| **Vyučující**      | Nejrychlejší pomoc při cvičení           |
| **Dokumentace**    | `help(funkce)` v Pythonu, oficiální docs |
| **Google**         | "how to find minimum in array Python"    |
| **Stack Overflow** | Téměř každý problém už někdo řešil       |
| **AI asistenti**   | Po zvládnutí základů                     |

### ✅ Self-check: Jsi připravený?

Než začneme programovat, zkontroluj, zda rozumíš základním konceptům:

| Otázka                                     | Odpověď                                                |
|--------------------------------------------|--------------------------------------------------------|
| Co je algoritmus?                          | Přesně definovaný postup s konečným počtem kroků       |
| Musí mít algoritmus vstup?                 | Ne, ale musí mít alespoň 1 výstup                      |
| Je `"Zahřej trochu"` dobrý krok algoritmu? | NE – není jednoznačný (kolik = trochu?)                |
| Proč používáme Python?                     | Jednoduchá syntaxe, obrovská komunita, AI/data science |
| Můžu používat AI hned od začátku?          | NE – nejdřív základy ručně, pak AI                     |
| Jak se naučím programovat?                 | Pouze programováním (praxe > teorie)                   |

---

## CÍL 1: INSTALACE A PŘÍPRAVA PROSTŘEDÍ (UV)

Pro správu našich projektů, knihoven a verzí Pythonu budeme používat nástroj `uv`. Tento nástroj nám výrazně zjednoduší práci s tzv. **virtuálními prostředími**.

> **Proč virtuální prostředí?**  
> Každý projekt může potřebovat jiné verze knihoven. Virtuální prostředí izoluje projekty od sebe – jako mít samostatný pracovní stůl pro každý projekt. Změny v jednom projektu neovlivní ostatní. Bez toho by aktualizace knihovny pro jeden projekt mohla rozbít všechny ostatní projekty.

### 1.1 Založení projektu a virtuálního prostředí

**Krok 1: Vytvoření složky pro projekt**

Nejprve si vytvoříme složku pro naše cvičení:

1. Otevřete **Průzkumník souborů** (File Explorer)
2. Přejděte na **Plochu** (Desktop)
3. Klikněte pravým tlačítkem do volného prostoru → **Nový** → **Složka**
4. Pojmenujte ji například `exercise01`

**Krok 2: Otevření PowerShellu ve složce**

Nyní musíme otevřít terminál (PowerShell) v této složce:

1. Otevřete složku `exercise01` (dvojklik)
2. Klikněte pravým tlačítkem do volného prostoru uvnitř složky
3. Zvolte **"Otevřít v terminálu"** (Open in Terminal) nebo **"Open in Windows Terminal"**

Otevře se okno PowerShellu s cestou k vaší složce (např. `C:\Users\Jméno\Desktop\exercise01>`).

**Krok 3: Instalace `uv`**

Nejprve musíme nástroj `uv` nainstalovat. Otevřete příkazovou řádku (Terminal) a spusťte následující příkaz (dle vašeho operačního systému):

> **💡 Instalace jen jednou:**
> Instalaci `uv` stačí provést **pouze jednou na každém počítači**. Pokud už máte `uv` nainstalovaný, přeskočte na sekci 1.2.
> 
> Pokud se přesunete na jiný školní počítač, budete muset `uv` nainstalovat znovu.

**Windows** (PowerShell):
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS / Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Po instalaci restartujte terminál a ověřte, že `uv` funguje příkazem:
```bash
uv --version
```

**Krok 4: Inicializace projektu**

V terminálu (PowerShellu) zadejte příkaz `uv init`. Tento příkaz vytvoří základní strukturu projektu:

Zadej do PowerShellu:

```bash
uv init
```

Po spuštění uvidíte, že v adresáři vznikly nové soubory, zejména:
- `main.py` – hlavní soubor s ukázkovým kódem
- `pyproject.toml` – konfigurační soubor projektu

**Krok 5: Vytvoření virtuálního prostředí**

Nyní vytvoříme virtuální prostředí pomocí příkazu `uv sync`:

Zadej do PowerShellu:

```bash
uv sync
```

Tento příkaz:
- Vytvoří složku `.venv` s virtuálním prostředím
- Nainstaluje Python (pokud není k dispozici)
- Připraví vše potřebné pro běh vašich programů

> **💡 Zobrazení přípony souborů a skrytých souborů:**
> 
> Pro programování je důležité vidět **přípony souborů** (`.py`, `.txt`) a **skryté soubory** (např. složku `.venv`).
> 
> **Jak to zapnout ve Windows:**
> 1. Otevřete **Průzkumník souborů** (File Explorer)
> 2. Klikněte na záložku **Zobrazení** (View) nahoře
> 3. Zaškrtněte:
>    - **Přípony názvů souborů** (File name extensions)
>    - **Skryté položky** (Hidden items)
> 
> **Alternativně (Windows 11):**
> - V Průzkumníku souborů klikněte na **⋯ (tři tečky)** → **Možnosti** → **Zobrazení**
> - V seznamu najděte a **odškrtněte**: "Skrýt přípony souborů známých typů"
> - Najděte a **zaškrtněte**: "Zobrazit skryté soubory, složky a jednotky"
> 
> **Proč je to důležité?**
> - Uvidíte, zda je soubor opravdu `.py` (a ne `.py.txt`)
> - Uvidíte složku `.venv` s virtuálním prostředím
> - Poznáte konfigurační soubory jako `.gitignore`

### 1.2 Práce v PyCharmu (konfigurace projektu)

Abychom mohli pohodlně psát kód a spouštět programy, otevřeme naši složku v prostředí PyCharm.

> **📥 Instalace PyCharm:**
> - **Na školních počítačích** je PyCharm již nainstalovaný
> - **Doma si PyCharm stáhněte** z [jetbrains.com/pycharm/download](https://www.jetbrains.com/pycharm/download/) a nainstalujte (vyberte správnou verzi podle vašeho operačního systému)

1.  Spusťte **PyCharm**.
2.  Na úvodní obrazovce zvolte **Open...** (nebo v menu **File > Open...**).
3.  Najděte a vyberte složku `exercise01`, kterou jsme připravili, a potvrďte **OK**.

> **💡 Co je to "projekt" v PyCharmu?**
> 
> PyCharm může při otevírání složky nabídnout vytvoření "projektu" (`.idea` složka s nastavením). Projekt v PyCharmu ukládá různá nastavení – jaký Python interpreter používáte, jaké máte otevřené soubory, kde máte záložky atd.
> 
> **Pro tento kurz to nepotřebujete** – můžete klidně otevřít složku "bez projektu" (This Window / Trust Project). Nastavení interpreteru si PyCharm zapamatuje i bez projektu. Pokud se projekt vytvoří, nic se nestane, `.idea` složku můžete ignorovat.

4.  **Nastavení interpretu (Pythonu):**
    *   PyCharm by měl automaticky detekovat složku `.venv`.
    *   Zkontrolujte vpravo dole v liště, zda vidíte verzi Pythonu (např. `Python 3.13 (exercise01)`).
    *   Pokud vidíte `<No interpreter>`, klikněte na něj → **Add New Interpreter** → **Add Local Interpreter...** → **Virtual Environment** ().
    *   Zvolte **Existing** a nalistujte cestu k `python.exe` ve vaší složce: `exercise01/.venv/Scripts/python.exe` (na Windows) nebo `exercise01/.venv/bin/python` (macOS/Linux).
    *   (V novějším PyCharmu zvolte **Existing**, Type: **uv**, Path to uv: `C:\Users\<login>\.local\bin\uv.exe` a nalistujte cestu k `python.exe` ve vaší složce: `exercise01/.venv/Scripts/python.exe` (na Windows) nebo `exercise01/.venv/bin/python` (macOS/Linux).)
Nyní PyCharm používá prostředí, které spravuje `uv`.

5.  Vypněte doplňování řádků:
    *   Otevřete nastavení **File > Settings...**.
    *   V levém sloupci rozklikněte možnost **Editor > General > Inline Completion**.
    *   Zrušte zaškrtnutí možnosti **Enable local Full Line completion suggestions**.

### 1.3 VUT disk
Ve školním počítači máte k dispozici osobní disk, tzv. VUT disk, obvykle namapovaný pod označením `V:`. Tento disk je soukromý a k jeho obsahu lze přistupovat pouze po zadání přihlašovacích údajů. To probíhá automaticky při přihlášení v počítačové učebně.

VUT disk je možné používat pro ukládání souborů ze cvičení tak, abyste k nim měli přístup i z domova. Pro přístup k tomuto disku mimo učebnu je nutné využít VPN. Podrobný návod k VUT disku najdete v Intraportálu [https://www.vut.cz/intra/vutdisk](https://www.vut.cz/intra/vutdisk).

---

## CÍL 2: PRVNÍ PROGRAM A ZÁKLADY SYNTAXE

Nyní se podíváme na samotný kód. Otevřete soubor `main.py`, který vidíte v levém panelu (Project View).

### 2.1 Hello World

Tradičně začínáme programem, který vypíše pozdrav. V Pythonu k tomu slouží funkce `print()`.

Když otevřete soubor `main.py`, uvidíte, že nám `uv` vygeneroval profesionální strukturu s funkcí `main()`. Pro začátek si to ale zjednodušíme. **Smažte celý obsah souboru** a napište pouze tento jeden řádek:

```python
print("Hello world!")
```

Program jednoduše spustíte stisknutím zelené šipky **Run** vpravo nahoře (nebo klávesovou zkratkou `Shift + F10`).

> **Poznámka:** Program lze spustit i v terminálu příkazem `python main.py`.

🎉 **Gratulujeme!** Právě jste spustili svůj první Python program. Může to vypadat jednoduše, ale každý programátor začínal právě tímto – výpisem "Hello World!". Od tohoto bodu vede cesta k jakékoliv aplikaci, kterou si dokážete představit.

Zkuste upravit text v uvozovkách na `"Hello Python!"` a spusťte program znovu.

> **💡 Tip: Jak organizovat kód při procvičování?**
> 
> Během cvičení budete psát mnoho programů. Máte dvě možnosti:
> 
> **1. Více souborů (doporučeno):**
> - V levém panelu (Project View) klikněte pravým tlačítkem na složku projektu
> - Zvolte **New → Python File** a pojmenujte soubor (např. `promenne.py`, `kalkulacka.py`)
> - PyCharm soubor vytvoří a otevře
> - Spustíte stejně jako `main.py` (zelená šipka nebo `Shift + F10`)
> - **Výhoda:** Máte přehled, můžete se vracet k starším příkladům
> 
> **2. Jeden soubor s komentováním:**
> - Když chcete zkusit nový kód, zakomentujte starý (`Ctrl + /`)
> - Napište nový kód pod něj
> - **Výhoda:** Vše na jednom místě, rychlé experimentování
> - **Nevýhoda:** Časem se v tom ztratíte
> 
> **Který způsob zvolit?** Pro úkoly vytvářejte nové soubory. Pro rychlé zkoušení syntaxe používejte komentování.

**O komentování:**  
Komentáře slouží k vysvětlení kódu a Python je ignoruje. Začínají znakem `#`.  

⌨️ **Klávesová zkratka:** **`Ctrl + /`** (označte řádky a stiskněte zkratku pro zakomentování/odkomentování).

```python
# Toto je komentář
print("Ahoj")  # Komentář může být i za příkazem
```

---

**📝 ÚKOL: Vytvoř svůj první soubor**

Vyzkoušej si vytvoření nového souboru:
1. Klikni pravým tlačítkem na složku projektu v levém panelu
2. Vyber **New → Python File**
3. Pojmenuj soubor `pozdrav.py`
4. Do nového souboru napiš:
   ```python
   # Můj první vlastní soubor
   print("Ahoj ze souboru pozdrav.py!")
   ```
5. Spusť program (zelená šipka)

💡 **Tip:** Všimni si, že PyCharm automaticky spustí nově vytvořený soubor.

---
                                                                                                                                                                                                                                          
### 💻 Důležité znaky pro programování

Při programování budete potřebovat speciální znaky. Zde je přehled, jak je napsat na **české** a **anglické** klávesnici:

| Znak | Název           | Česká klávesnice                                                      | Anglická klávesnice                                  |
|------|-----------------|-----------------------------------------------------------------------|------------------------------------------------------|
| `#`  | Hash (mřížka)   | pravý <kbd>Alt</kbd> + <kbd>X</kbd>                                   | <kbd>Shift</kbd> + <kbd>3</kbd>                      |
| `()` | Kulaté závorky  | <kbd>Shift</kbd> + <kbd>)</kbd>/<kbd>)</kbd> (vedle <kbd>Enter</kbd>) | <kbd>Shift</kbd> + <kbd>9</kbd>/<kbd>0</kbd>         |
| `[]` | Hranaté závorky | pravý <kbd>Alt</kbd> + <kbd>F</kbd>/<kbd>G</kbd>                      | <kbd>[</kbd>/<kbd>]</kbd>                            |
| `{}` | Složené závorky | pravý <kbd>Alt</kbd> + <kbd>B</kbd>/<kbd>N</kbd>                      | <kbd>Shift</kbd> + <kbd>[</kbd>/<kbd>]</kbd>         |
| `<>` | Lomené závorky  | pravý <kbd>Alt</kbd> + <kbd>,</kbd>/<kbd>.</kbd>                      | <kbd>Shift</kbd> + <kbd>,</kbd>/<kbd>.</kbd>         |
| `/`  | Lomítko         | <kbd>/</kbd>                                                          | <kbd>/</kbd>                                         |
| `\`  | Zpětné lomítko  | pravý <kbd>Alt</kbd> + <kbd>Q</kbd>                                   | <kbd>\\</kbd>                                        |
| `_`  | Podtržítko      | <kbd>Shift</kbd> + <kbd>-</kbd>                                       | <kbd>Shift</kbd> + <kbd>-</kbd> (vedle <kbd>0</kbd>) |
| `:`  | Dvojtečka       | <kbd>Shift</kbd> + <kbd>.</kbd>                                       | <kbd>Shift</kbd> + <kbd>;</kbd>                      |
| `;`  | Středník        | <kbd>;</kbd> (nad <kbd>Tab</kbd>)                                     | <kbd>;</kbd>                                         |
| `"`  | Uvozovky        | <kbd>Shift</kbd> + <kbd>ů</kbd>                                       | <kbd>Shift</kbd> + <kbd>'</kbd>                      |
| `'`  | Apostrof        | <kbd>Shift</kbd> + <kbd>¨</kbd>                                       | <kbd>'</kbd>                                         |
             
> **💡 Proč programátoři často používají anglickou klávesnici?**  
> Speciální znaky potřebné pro programování (`{}`, `[]`, `/`, `\`) jsou na anglické klávesnici **mnohem dostupnější** – většinou stačí jeden <kbd>Shift</kbd> místo pravého <kbd>Alt</kbd> kombinací. To výrazně zrychluje psaní kódu. Pokud hodně programujete, zvažte přepnutí layoutu na US International (ale každému vyhovuje něco jiného).

> **⚠️ Pozor na klávesu <kbd>Insert</kbd>!**  
> Pokud omylem stisknete <kbd>Insert</kbd>, přepne se režim na přepisování - poznáte to podle **širšího kurzoru** (místo tenké čárky). Nový text pak přepisuje existující znaky místo vkládání. Vypnete stisknutím <kbd>Insert</kbd> znovu.

---

### 2.2 Proměnné (Variables)

Proměnná slouží k uložení hodnoty (čísla, textu). V Pythonu nemusíme určovat typ proměnné předem, pozná se automaticky.

Příklad (doplňte do svého souboru místo předchozího kódu):
```python
name = "Petr"
age = 20
greeting = "Ahoj" 

print(greeting)
print(name)
print(f"Věk: {age}")  # f-string: elegantnejsi zpusob vypisu promennych
```

> **Poznámka o f-stringových literálech (f-string):**  
> Před uvozovky napíšeme `f` a do složených závorek `{}` můžeme vložit proměnnou nebo výraz. Python automaticky převede hodnotu na text a vloží ji do řetězce.  



**Pravidla pro pojmenování proměnných podle PEP 8:**

> **📘 Co je PEP 8?**  
> **PEP 8** (Python Enhancement Proposal 8) je **oficiální průvodce stylem** pro psaní kódu v Pythonu. Definuje konvence, jak má vypadat "hezký" a čitelný Python kód – od mezer kolem operátorů přes pojmenování proměnných až po délku řádků.
> 
> **Proč PEP 8 dodržovat?**
> - **Čitelnost:** Váš kód vypadá jako ostatní Python kód → ostatní ho snáze pochopí
> - **Profesionalita:** Dodržování PEP 8 je standard v celém Python ekosystému
> - **Spolupráce:** V týmových projektech všichni píší stejným stylem
> - **AI nástroje:** GitHub Copilot a podobné nástroje očekávají PEP 8 styl
> 
> 📖 Plný text najdete na: [python.org/dev/peps/pep-0008](https://peps.python.org/pep-0008/)
> 
> **Pro začátečníky:** Zatím se soustředíme na základní pravidla níže. S pokročilými konvencemi se seznámíte postupně.


1.  **Snake case pro proměnné a funkce**: Názvy píšeme **malými písmeny**, slova oddělujeme **podtržítkem** (`_`).
    ```python
    # ✅ SPRÁVNĚ (snake_case)
    user_name = "Marie"
    total_score = 150
    patient_temperature = 37.5
    is_valid = True
    
    # ❌ ŠPATNĚ (camelCase - používá se v Javě/JavaScriptu)
    userName = "Marie"
    totalScore = 150
    
    # ❌ ŠPATNĚ (PascalCase - v Pythonu jen pro třídy)
    UserName = "Marie"
    TotalScore = 150
    ```
    
2.  **Konstanty velkými písmeny**: Hodnoty, které se **nemění**, píšeme **VELKÝMI_PÍSMENY**.
    ```python
    # Konstanty - obvykle se definují na začátku souboru
    MAX_SPEED = 120
    PI = 3.14159
    DEFAULT_TEMPERATURE = 36.6
    ```
    
3.  **Výstižnost před stručností**: Název by měl **popisovat obsah** – raději delší a jasný než krátký a nejasný.
    ```python
    # ✅ SPRÁVNĚ - jasné
    patient_age = 65
    heart_rate_bpm = 72
    
    # ❌ ŠPATNĚ - co znamená "p", "a", "hr"?
    p = 65
    a = 65
    hr = 72
    ```
    
4.  **Angličtina**: Mezinárodní standard – usnadní spolupráci a použití ve větších projektech.
    ```python
    # ✅ DOPORUČENO
    temperature = 37.5
    patient_name = "Jan Novák"
    
    # ⚠️ Funguje, ale není standard (pro školní projekty OK)
    teplota = 37.5
    jmeno_pacienta = "Jan Novák"
    ```
    > V tomto kurzu můžete v učebních příkladech používat i české názvy pro lepší pochopení. V reálných projektech ale preferujte angličtinu.
    
5.  **Bez diakritiky**: Python sice zvládá háčky a čárky, ale lepší je se jim vyhnout.
    ```python
    # ✅ SPRÁVNĚ
    cislo = 42
    vysledek = 100
    
    # ❌ ŠPATNĚ (technicky funguje, ale není doporučeno)
    číslo = 42
    výsledek = 100
    ```
    
6.  **Nezačínat číslem**: Proměnná nesmí začínat číslicí.
    ```python
    # ✅ SPRÁVNĚ
    place_1 = "zlato"
    patient_001 = "Jan Novák"
    
    # ❌ CHYBA - nelze zkompilovat
    1_place = "zlato"
    001_patient = "Jan Novák"
    ```
    
7.  **Nepřepisujte vestavěné funkce**: Nepoužívejte názvy, které v Pythonu už něco znamenají (`print`, `len`, `list`, `str`, `sum`, `max`, `min`...).
    ```python
    # ❌ ŠPATNĚ - přepíše vestavěnou funkci
    print = "Nějaký text"  
    print("Ahoj")  # CHYBA! print už není funkce, ale text!
    
    # ✅ SPRÁVNĚ
    message = "Nějaký text"
    output_text = "Nějaký text"
    print(message)  # Funguje korektně
    ```

> **💡 Poznámka o podtržítcích:**  
> - **Podtržítko na začátku** (`_internal`, `__private`): Označuje "interní" proměnné. Používá se až v pokročilejším programování při tvorbě modulů a tříd.  
> - **Podtržítko na konci** (`class_`, `type_`): Používá se, když chceme použít název, který je rezervované klíčové slovo Pythonu (např. `class`, `type`, `list` jsou rezervované, takže použijeme `class_`, `type_`, `list_`).

---

**📝 ÚKOL: První proměnná**

Vytvořte proměnnou `course` s hodnotou `"Algoritmizace"` a vypište větu:  
```
Vítejte v kurzu Algoritmizace
```

💡 **Tip:** Použijte proměnnou uvnitř funkce `print()` (například pomocí f-stringu).

---

### 2.3 Matematické operátory

Python funguje skvěle jako kalkulačka. K dispozici máme základní operátory:

| Operace                        | Znak | Příklad  | Výsledek |
|--------------------------------|------|----------|----------|
| Sčítání                        | `+`  | `5 + 3`  | `8`      |
| Odčítání                       | `-`  | `10 - 2` | `8`      |
| Násobení                       | `*`  | `4 * 2`  | `8`      |
| Dělení (vrací desetinné číslo) | `/`  | `10 / 2` | `5.0`    |
| Celočíselné dělení             | `//` | `7 // 3` | `2`      |
| Zbytek po dělení (modulo)      | `%`  | `7 % 3`  | `1`      |
| Umocnění                       | `**` | `2 ** 3` | `8`      |

```python
# Vyzkoušejte si různé operátory
print(2 + 3)      # 5
print(10 - 20)    # -10
print(2 * 5)      # 10
print(10 / 3)     # 3.333...
print(10 // 3)    # 3 (celočíselné dělení)
print(10 % 3)     # 1 (zbytek)
print(2 ** 6)     # 64 (dvě na šestou)
```

**Praktický příklad:**
```python
# Výpočet BMI (Body Mass Index)
weight = 75  # kg
height = 1.80  # m

bmi = weight / (height ** 2)
print(f"Vaše BMI: {bmi}")  # Vypíše na 1 des. místo
```

**Příklad: Zbytek po dělení (modulo)**

Modulo `%` nám vrátí zbytek po celočíselném dělení. Hodí se např. k určení, zda je číslo sudé.

```python
number = 14
divisor = 3

remainder = number % divisor
print(f"Číslo {number} děleno {divisor} má zbytek {remainder}")
```

---

**📝 ÚKOL: Výpočet daně z příjmu**

Představte si, že máte měsíční příjem 25 000 Kč a chcete spočítat, kolik zaplatíte na dani za celý rok. Daňová sazba je 15 %.

Vytvořte program, který:
1. Definuje konstanty `MONTHS = 12` a `TAX_RATE_PCT = 15`
2. Vytvoří proměnnou `monthly_income = 25000`
3. Vypočítá roční příjem (měsíční příjem × počet měsíců)
4. Převede procenta na desetinné číslo (15 % → 0.15)
5. Vypočítá celkovou daň (roční příjem × daňová sazba)
6. Vypíše oba výsledky pomocí f-stringu

---

### 2.4 Logické operátory

Kromě počítání často potřebujeme hodnoty porovnávat. Výsledkem je vždy `True` (pravda) nebo `False` (nepravda).

| Operace          | Znak | Příklad   | Výsledek |
|------------------|------|-----------|----------|
| Rovnost          | `==` | `5 == 5`  | `True`   |
| Nerovnost        | `!=` | `5 != 3`  | `True`   |
| Větší než        | `>`  | `5 > 5`   | `False`  |
| Menší než        | `<`  | `2 < 5`   | `True`   |
| Větší nebo rovno | `>=` | `5 >= 5`  | `True`   |
| Menší nebo rovno | `<=` | `4 <= -5` | `False`  |

```python
# Vyzkoušejte porovnání
print(5 > 2)      # True
print(10 == 10)   # True
print(5 != 5)     # False
print(3 < 2)      # False
print(7 <= 10)    # True
```

**Praktický příklad:**
```python
temperature = 38.5

has_fever = temperature >= 38.0
print(f"Horečka: {has_fever}")  # Vypíše True nebo False
```

### 2.5 Seznamy a indexace

**Seznam** (list) je sbírka hodnot uzavřená v hranatech závorkách `[]`. Můžeme v něm mít čísla, texty, nebo cokoliv jiného.

```python
# Seznam teplot pacientů
temperatures = [36.6, 37.2, 38.1, 36.9, 37.5]

# Přístup k jednotlivým prvkům pomocí indexu (začíná od 0!)
print(temperatures[0])  # 36.6 (první prvek)
print(temperatures[1])  # 37.2 (druhý prvek)
print(temperatures[4])  # 37.5 (pátý prvek)
```

> ⚠️ **Důležité:** Indexování začíná od **0**, ne od 1! První prvek je `seznam[0]`, druhý je `seznam[1]` atd.

#### Funkce len() - zjištění délky

Funkce `len()` nám řekne, **kolik prvků** je v seznamu (nebo kolik znaků v textu).

```python
# Délka seznamu
temperatures = [36.6, 37.2, 38.1, 36.9, 37.5]
count = len(temperatures)
print(f"Máme {count} měření teploty")  # Máme 5 měření teploty

# Délka textu (počet znaků včetně mezer)
name = "Jan Novák"
length = len(name)
print(f"Jméno má {length} znaků")  # Jméno má 9 znaků
```

**Praktický příklad:**
```python
patients = ["Jan Novák", "Marie Svobodová", "Petr Dvořák"]

first_patient = patients[0]
second_patient = patients[1]

print(f"První pacient: {first_patient}")
print(f"Druhý pacient: {second_patient}")
```

### 2.6 Jednoduché podmínky a odsazování

Podmínky nám umožňují větvit program – vykonat určitou část kódu jen tehdy, když platí nějaký předpoklad.

#### Odsazování (Indentation)

V Pythonu je odsazování **klíčové** pro strukturu programu. Určuje, které příkazy patří do bloku (např. do podmínky nebo cyklu).
*   Používáme **4 mezery** (nebo 1 tabulátor, ale nemíchejte to!).
*   ⌨️ **Klávesové zkratky:**
    *   **`Tab`** – odsadí řádek (přidá 4 mezery)
    *   **`Shift + Tab`** – odsune řádek zpět (odebere 4 mezery)
    *   **Tip:** Můžete označit více řádků a odsadit/odsunout je najednou!

#### Podmínky if/else

Používáme klíčová slova `if` (když) a `else` (jinak). Důležité je **odsazení** kódu pod podmínkou!

```python
number = 10

if number > 5:
    print("Číslo je větší než 5")     # Odsazený řádek = patří do podmínky
else:
    print("Číslo je menší nebo rovno 5")
```

**Praktický příklad:**
```python
temperature = 38.5

# Detekce horečky (>= 38 °C)
if temperature >= 38.0:
    print("Pacient má horečku!")
else:
    print("Teplota v normě")
```

---

**📝 ÚKOL: Kontrola srdeční frekvence**

Napište program, který kontroluje srdeční frekvenci pacienta. 

Vytvořte:
- Proměnnou `heart_rate` s hodnotou 105 (tepů za minutu)
- Konstantu `TACHYCARDIA_LIMIT = 100` (hranice pro zrychlený tep)

Program má pomocí podmínky zkontrolovat, zda je `heart_rate` větší než limit, a vypsat:
- Pokud ANO: `"Zrychlený tep: 105 tepů/min (limit: 100)"`
- Pokud NE: `"Srdeční frekvence v normě"`

💡 **Tip:** Použijte f-stringy pro výpis hodnot proměnných.

---

### 2.7 Cyklus for

Cyklus `for` nám umožňuje opakovat určitou činnost pro prvky v nějaké skupině. Nejprve si ukážeme opakování pomocí čísel.

#### For s range()
Funkce `range(n)` vygeneruje čísla od 0 do *n*-1.

```python
# Vypíše "Ahoj" 5x pod sebou a pak se rozloučí
for i in range(5):
    print(f"Ahoj {i}")
    print("...další řádek v cyklu (taky odsazený)")

print("Toto se vypíše až po skončení cyklu (už není odsazené).")
```

Řídící proměnná `i` v každém kroku cyklu nabývá nové hodnoty (`0`, `1`, `2`, `3`, `4`).

#### For se seznamem

Již víme, že seznam je sbírka hodnot (viz sekce 2.5). Nyní si ukážeme, jak projít **všechny** prvky v seznamu pomocí cyklu `for`.

```python
# Seznam oblíbených ovoce
fruits = ["jablko", "hruška", "banán", "pomeranč"]

# Projdeme všechny položky a vypíšeme je
for fruit in fruits:
    print(f"Mám rád {fruit}")
```

Výstup bude:
```
Mám rád jablko
Mám rád hruška
Mám rád banán
Mám rád pomeranč
```

V každém kroku cyklu proměnná `fruit` dostane hodnotu jednoho prvku ze seznamu.

---

**📝 ÚKOL 1: Kontrola lůžek na oddělení**

Na oddělení je 10 lůžek očíslovaných od 0 do 9. Napište program, který pomocí cyklu `for` vypíše všechna čísla lůžek ve formátu:

```
Lůžko č. 0
Lůžko č. 1
Lůžko č. 2
...
```

💡 **Tip:** Použijte `range(10)` a f-string pro výpis.

---

**📝 ÚKOL 2: Výpis teplot pacientů**

Vytvořte seznam `temperatures` s alespoň 5 hodnotami teplot (např. `[36.6, 37.2, 38.1, 36.9, 37.5]`).  

Pomocí cyklu `for` projděte všechny teploty a vypište je ve formátu:  
```
Teplota: 36.6 °C
```

💡 **Tip:** Použijte `for temp in temperatures:` pro průchod seznamem.

---

### 2.8 Co když udělám chybu? (Chyby a jejich řešení)

Chyby jsou **přirozenou součástí** programování. Nikdo nepíše dokonalý kód napoprvé! Důležité je umět chyby **číst, pochopit a opravit**.

#### Typy chyb

**1. Syntaktická chyba (SyntaxError)**  
Porušení pravidel jazyka Python – např. chybějící dvojtečka, špatné odsazení.

```python
# ❌ CHYBA: Chybí dvojtečka za if
if temperature > 38
    print("Horečka")
```

**Chybová hláška:**
```
  File "main.py", line 1
    if temperature > 38
                       ^
SyntaxError: expected ':'
```

**Jak opravit:** Přidejte dvojtečku: `if temperature > 38:`

---

**2. Chyba názvu (NameError)**  
Použití neexistující proměnné nebo funkce.

```python
# ❌ CHYBA: Proměnná 'age' neexistuje
print(f"Věk: {age}")
```

**Chybová hláška:**
```
NameError: name 'age' is not defined
```

**Jak opravit:** Definujte proměnnou před použitím: `age = 20`

---

**3. Chyba typu (TypeError)**  
Nekompatibilní operace mezi datovými typy.

```python
# ❌ CHYBA: Nelze sčítat text a číslo
result = "Věk: " + 25
```

**Chybová hláška:**
```
TypeError: can only concatenate str (not "int") to str
```

**Jak opravit:** Použijte f-string: `result = f"Věk: {25}"`

---

**4. Chyba odsazení (IndentationError)**  
Špatné odsazení kódu.

```python
# ❌ CHYBA: Špatné odsazení
if True:
print("Ahoj")
```

**Chybová hláška:**
```
File "<input>", line 2
    print("Ahoj")
    ^
IndentationError: expected an indented block after 'if' statement on line 1
```

**Jak opravit:** Odsaďte řádek `print("Ahoj")` 4 mezerami (nebo Tab).

---

#### Jak číst chybové hlášky (Traceback)

Když Python narazí na chybu, vypíše **Traceback** (zpětné trasování):

```
Traceback (most recent call last):
  File "main.py", line 5, in <module>
    print(f"Výsledek: {result}")
NameError: name 'result' is not defined
```

**Důležité informace:**
1. **Soubor a řádek:** `File "main.py", line 5` → Chyba je na řádku 5
2. **Kód:** `print(f"Výsledek: {result}")` → Toto způsobilo chybu
3. **Typ chyby:** `NameError: name 'result' is not defined` → Proměnná `result` neexistuje

---

#### Tipy pro ladění (debugging)

✅ **Čtěte chybu pozorně** – Python říká, co je špatně  
✅ **Začněte od spodu** – Poslední řádek Tracebacku obsahuje hlavní info  
✅ **Kontrolujte číslo řádku** – Chyba může být i na jiném řádku, Python jen oznámí, kde skončil  
✅ **Testujte po malých krocích** – Nečekejte se spuštěním, až napíšete 50 řádků  
✅ **Použijte `print()`** – Vypisujte hodnoty proměnných pro kontrolu

**Příklad ladění:**
```python
temperature = 38.5
# Kontrolní výpis (debugging)
print(f"DEBUG: Teplota = {temperature}")  

if temperature > 38.0:
    print("Horečka detekována")
```

---

**📝 ÚKOL: Detektiv chyb**

Následující 4 kódy obsahují chyby. Vaším úkolem je:
1. **Zkopírovat každý kód do PyCharmu**
2. **Spustit ho** a přečíst si chybovou hlášku
3. **Opravit chybu** podle toho, co Python vypíše
4. **Spustit znovu** a ověřit, že kód funguje

**Kód 1:**
```python
heart_rate = 72
if heart_rate > 100
    print("Tachykardie!")
```

**Kód 2:**
```python
patient_name = "Jan Novák"
print(f"Pacient: {pacient_name}")
```

**Kód 3:**
```python
temperature = 37.5
if temperature > 38.0:
print("Horečka!")
```

**Kód 4:**
```python
temperatures = [36.6, 37.2, 38.1]
first_temp = temperatures[0]
last_temp = temperatures[3]
print(last_temp)
```

💡 **Tip:** Každá chyba odpovídá jednomu z typů chyb popsaných výše. Přečtěte si chybovou hlášku pozorně – Python vám napoví, co je špatně!

> **Zlaté pravidlo:** Pište kód po malých částech (3-5 řádků) a průběžně testujte. Nenechávejte testování až na konec!

---

## CÍL 3: POKROČILÉ PODMÍNKY 

### 3.1 Spojování podmínek (Logické operátory)

V předchozím cíli jsme se naučili porovnávat hodnoty (`>`, `<`, `==`, ...). Nyní si ukážeme, jak spojíme více podmínek dohromady.

| Operátor | Význam                     | Příklad             | Výsledek |
|----------|----------------------------|---------------------|----------|
| `and`    | A zároveň (platí obojí)    | `5 > 0 and 1 < 10`  | `True`   |
| `or`     | Nebo (platí alespoň jedno) | `1 == 1 or 10 == 2` | `True`   |
| `not`    | Negace (opak)              | `not (10 > 5)`      | `False`  |

```python
# Vyzkoušejte logické operátory
print(True and False)   # False (musí platit OBĚ)
print(True or False)    # True (stačí JEDNO)
print(not True)         # False (opak)
```

**Rozšíření předchozího příkladu s horečkou:**

V sekci 2.6 jsme kontrolovali pouze horečku. Nyní si ukážeme, jak zkontrolovat, zda je teplota v normálním rozmezí (36-37 °C) pomocí `and`.

```python
temperature = 36.8

# Kontrola normální teploty (36-37 °C) - musí platit OBĚ podmínky
if temperature >= 36.0 and temperature <= 37.0:
    print("Normální teplota")
else:
    print("Teplota mimo normu")
```

---

**📝 ÚKOL: Varovný systém vitálních funkcí**

Napište program, který zkontroluje, zda je potřeba zavolat lékaře.

Vytvořte proměnné:
- `temperature = 39.2` (teplota v °C)
- `heart_rate = 105` (srdeční frekvence)

Lékaře zavolejte, pokud **ALESPOŇ JEDNA** z následujících podmínek platí:
- Teplota je >= 39.0 °C (vysoká horečka)
- Srdeční frekvence je > 110 tepů/min

Program má vypsat:
- `"VAROVÁNÍ: Zavolejte lékaře!"` pokud platí alespoň jedna podmínka
- `"Vitální funkce v pořádku"` pokud jsou obě hodnoty v normě

💡 **Tip:** Použijte operátor `or` pro spojení podmínek.

---

## CÍL 4: KOMBINACE CYKLU A PODMÍNEK

Nyní si ukážeme, jak spojit cykly s podmínkami. To je velmi mocný nástroj - umožňuje nám projít data a reagovat odlišně na každý prvek.

### 4.1 Podmínka uvnitř cyklu

Základní princip je jednoduchý: cyklem projdeme všechny prvky a podmínkou rozhodneme, co s nimi uděláme.

**Příklad: Detekce horečky u pacientů**

```python
# Seznam teplot pacientů
temperatures = [36.6, 38.5, 37.2, 39.1, 36.9]

# Projdeme všechny teploty
for temp in temperatures:
    if temp >= 38.0:
        print(f"Horečka: {temp} °C")
    else:
        print(f"V normě: {temp} °C")
```

Výstup:
```
V normě: 36.6 °C
Horečka: 38.5 °C
V normě: 37.2 °C
Horečka: 39.1 °C
V normě: 36.9 °C
```

**Příklad: Počítání problémových hodnot**

```python
# Seznam teplot
temperatures = [36.6, 38.5, 37.2, 39.1, 36.9, 38.2]

# Počítadlo pacientů s horečkou
fever_count = 0

for temp in temperatures:
    if temp >= 38.0:
        fever_count += 1  # Zkrácený zápis pro: fever_count = fever_count + 1

print(f"Celkem pacientů: {len(temperatures)}")
print(f"Pacientů s horečkou: {fever_count}")
```

> **💡 Operátor `+=`:** Zkrácený zápis pro přičítání. `x += 1` je totéž jako `x = x + 1`.

---

**📝 ÚKOL: Kontrola lékařských vzorků**

V laboratoři máte vzorky s různými hodnotami glykémie (cukru v krvi).  
Normální hodnota je 3.9-5.6 mmol/l.

Napište program, který:
1. Vytvoří seznam `glucose_levels = [4.5, 6.2, 3.8, 5.1, 7.5, 4.9]`
2. Projde všechny hodnoty pomocí cyklu
3. Pro každou hodnotu:
   - Pokud je **pod 3.9**: vypíše `"Hypoglykémie: X mmol/l"`
   - Pokud je **nad 5.6**: vypíše `"Hyperglykémie: X mmol/l"`
   - Jinak: vypíše `"V normě: X mmol/l"`

💡 **Tip:** Budete potřebovat vnořené podmínky (`if` uvnitř `else`).

---

## ZÁVĚREČNÉ ÚKOLY

Nyní si vyzkoušíte vše, co jste se naučili v tomto cvičení. Vytvořte si nový soubor pro každý úkol.

### ÚKOL 1: Analýza teplot na oddělení

Napište program, který analyzuje teploty pacientů na oddělení za jeden den.

**Zadání:**
1. Vytvořte seznam měření: `temperatures = [36.6, 38.5, 37.2, 39.1, 36.9, 38.2, 37.5, 40.1]`
2. Vytvořte konstanty:
   - `FEVER_LIMIT = 38.0` (hranice pro horečku)
   - `HIGH_FEVER_LIMIT = 39.5` (hranice pro vysokou horečku)
3. Vytvořte počítadla: `normal_count = 0`, `fever_count = 0`, `high_fever_count = 0`
4. Projděte všechny teploty cyklem a pro každou:
   - Pokud je >= HIGH_FEVER_LIMIT: zvyšte `high_fever_count`
   - Pokud je >= FEVER_LIMIT (ale < HIGH_FEVER_LIMIT): zvyšte `fever_count`
   - Jinak: zvyšte `normal_count`
5. Vypište statistiku:
   ```
   === ANALÝZA TEPLOT ===
   Celkem měření: 8
   Normální teplota: 3
   Horečka: 3
   Vysoká horečka: 2
   ```

💡 **Použijte:** seznamy, cykly, podmínky, operátor `+=`, f-stringy

---

### ÚKOL 2: Kontrola BMI pacientů

Napište program, který vyhodnotí BMI (Body Mass Index) pro seznam pacientů.

**Zadání:**
1. Vytvořte seznamy:
   - `weights = [75, 68, 92, 58, 80]` (váhy v kg)
   - `heights = [1.80, 1.65, 1.90, 1.60, 1.75]` (výšky v metrech)
2. Vytvořte počítadlo: `overweight_count = 0`
3. Projděte všechny pacienty pomocí `range(5)`:
   - Vypočítejte BMI: `bmi = weights[i] / (heights[i] ** 2)`
   - Vypište: `"Pacient 1: BMI = 23.1"`
   - Pokud je BMI >= 25: zvyšte `overweight_count`
4. Na konci vypište: `"Počet pacientů s nadváhou: X"`

💡 **Použijte:** seznamy, indexaci, cyklus `range()`, matematické operace, podmínky

**Vzorec:** BMI = váha / (výška²)  
**Hranice:** BMI >= 25 znamená nadváhu

---

## 🌟 BONUSOVÉ ÚKOLY

Tyto úkoly jsou pro ty, kteří chtějí procvičit nabyté znalosti nad rámec povinných úkolů.

### BONUS 1: Analýza krevního tlaku

Napište program pro vyhodnocení krevního tlaku pacientů.

**Zadání:**
1. Vytvořte dva seznamy:
   - `systolic = [120, 140, 135, 110, 155, 125, 145]` (horní tlak)
   - `diastolic = [80, 90, 85, 70, 95, 82, 92]` (dolní tlak)
2. Vytvořte konstanty:
   - `NORMAL_SYS_LIMIT = 130` (hranice normálního horního tlaku)
   - `NORMAL_DIA_LIMIT = 85` (hranice normálního dolního tlaku)
3. Vytvořte počítadla: `normal_count = 0`, `high_count = 0`
4. Projděte všechny měření pomocí `range(len(systolic))`:
   - Vypište: `"Pacient X: 120/80 mmHg"`
   - Pokud je **ALESPOŇ JEDNO** z měření mimo normu (systolic >= 130 **nebo** diastolic >= 85):
     - Vypište: `"  Zvýšený tlak"`
     - Zvyšte `high_count`
   - Jinak:
     - Vypište: `"  Normální"`
     - Zvyšte `normal_count`
5. Na konci vypište statistiku:
   ```
   === SOUHRN ===
   Normální tlak: X pacientů
   Zvýšený tlak: Y pacientů
   ```

💡 **Použijte:** dva seznamy, indexaci, `range()`, logický operátor `or`, f-stringy

---

### BONUS 2: Výpočet průměrné srdeční frekvence

Napište program, který spočítá průměrnou srdeční frekvenci a najde extrémní hodnoty (minimální a maximální).

**Zadání:**
1. Vytvořte seznam měření: `heart_rates = [72, 85, 68, 105, 78, 92, 70, 88]`
2. Inicializujte proměnné:
   - `total = 0` (pro součet všech hodnot)
   - `min_rate = heart_rates[0]` (minimální hodnota - nejprve přiřadíme první hodnotu)
   - `max_rate = heart_rates[0]` (maximální hodnota - nejprve přiřadíme první hodnotu)
3. Projděte všechna měření cyklem:
   - Přičtěte hodnotu k `total`
   - Pokud je hodnota menší než `min_rate`, aktualizujte `min_rate`
   - Pokud je hodnota větší než `max_rate`, aktualizujte `max_rate`
4. Vypočítejte průměr: `average = total / len(heart_rates)`
5. Vypište výsledky:
   ```
   === ANALÝZA SRDEČNÍ FREKVENCE ===
   Počet měření: 8
   Průměrná hodnota: 82.2 tepů/min
   Minimum: 68 tepů/min
   Maximum: 105 tepů/min
   ```

💡 **Použijte:** seznamy, cyklus, podmínky, matematické operace, `len()`, formátování na 1 desetinné místo

**Hint:** Pro výpis s 1 des. místem: `f"{average:.1f}"`

---

## SHRNUTÍ
V tomto cvičení jsme se naučili:
1.  **Pracovat s nástroji**: Vytvořit projekt pomocí `uv init`, nastavit PyCharm a spouštět kód.
2.  **Psát čistý kód**: Dodržovat pravidla pro názvy proměnných (snake_case) a správně odsazovat kód.
3.  **Řídit tok programu**: Používat podmínky `if/else` a cykly `for`.
4.  **Počítat**: Využívat matematické (+, -, *, /, %, **) a logické (==, !=, <, >, <=, >=, and, or, not) operátory.
5.  **Pracovat se seznamy**: Vytvářet seznamy, indexovat je a procházet cykly.
6.  **Kombinovat koncepty**: Spojovat cykly s podmínkami pro složitější úlohy.
7.  **Řešit chyby**: Číst chybové hlášky a hledat číslo řádku s chybou.

---

## 📝 SELF-CHECK: PROCVIČENÍ ZNALOSTÍ

### Část A: Teoretické otázky (vyberte správnou odpověď)

**1. Co udělá příkaz `uv init`?**
- a) Spustí Python program
- b) Vytvoří nový projekt se základní strukturou
- c) Nainstaluje Python
- d) Otevře PyCharm

<details>
<summary>✅ Správná odpověď</summary>
b) Vytvoří nový projekt se základní strukturou (včetně pyproject.toml a main.py)
</details>

**2. Jak napíšete znak `#` na české klávesnici?**
- a) `Shift + 3`
- b) `pravý Alt + X`
- c) `Ctrl + 3`
- d) `Alt + X`

<details>
<summary>✅ Správná odpověď</summary>
b) `pravý Alt + X` (na anglické klávesnici je to `Shift + 3`)
</details>

**3. Jak se správně pojmenovává proměnná v Pythonu?**
- a) `MonthlyIncome`
- b) `monthly-income`
- c) `monthly_income`
- d) `MONTHLY_INCOME`

<details>
<summary>✅ Správná odpověď</summary>
c) `monthly_income` (snake_case - pro běžné proměnné)
</details>

**4. Co se stane, když omylem stisknete klávesu Insert?**
- a) Smaže celý kód
- b) Přepne na přepisovací režim (širší kurzor)
- c) Uloží soubor
- d) Nic

<details>
<summary>✅ Správná odpověď</summary>
b) Přepne na přepisovací režim - poznáte podle širšího kurzoru místo tenké čárky
</details>

**5. Co vypíše tento kód?**
```python
temperatures = [36.6, 37.2, 38.1]
print(temperatures[0])
```
- a) `36.6`
- b) `37.2`
- c) `[36.6, 37.2, 38.1]`
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
a) `36.6` (první prvek seznamu, indexujeme od 0)
</details>

**4. Co vrátí `5 % 2`?**
- a) 2.5
- b) 2
- c) 1
- d) 0

<details>
<summary>✅ Správná odpověď</summary>
c) 1 (zbytek po dělení 5 ÷ 2)
</details>

**5. Co vrátí `len([10, 20, 30, 40])`?**
- a) 10
- b) 40
- c) 3
- d) 4

<details>
<summary>✅ Správná odpověď</summary>
d) 4 (počet prvků v seznamu)
</details>

**6. Jaký je rozdíl mezi `and` a `or`?**
- a) `and` vyžaduje obě podmínky, `or` alespoň jednu
- b) `and` je rychlejší než `or`
- c) Žádný rozdíl
- d) `or` vyžaduje obě podmínky

<details>
<summary>✅ Správná odpověď</summary>
a) `and` vyžaduje, aby platily OBĚ podmínky, `or` stačí, když platí alespoň jedna
</details>

**7. Co vypíše `print(f"Teplota: {38.5} °C")`?**
- a) `f"Teplota: {38.5} °C"`
- b) `Teplota: {38.5} °C`
- c) `Teplota: 38.5 °C`
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
c) `Teplota: 38.5 °C` (f-string automaticky dosadí hodnotu ze závorek)
</details>

**8. Jak pojmenujeme konstantu (hodnotu, která se nemění)?**
- a) `maxSpeed`
- b) `max_speed`
- c) `MAX_SPEED`
- d) `Max_Speed`

<details>
<summary>✅ Správná odpověď</summary>
c) `MAX_SPEED` (konstanty píšeme velkými písmeny)
</details>

**9. Co vrátí `2 ** 3`?**
- a) 5
- b) 6
- c) 8
- d) 9

<details>
<summary>✅ Správná odpověď</summary>
c) 8 (mocnění: 2³ = 2 × 2 × 2 = 8)
</details>

**10. Co vrátí `10 // 3`?**
- a) 3.333...
- b) 3
- c) 4
- d) 1

<details>
<summary>✅ Správná odpověď</summary>
b) 3 (celočíselné dělení - vrací jen celou část)
</details>

**11. Který operátor kontroluje rovnost?**
- a) `=`
- b) `==`
- c) `===`
- d) `equals`

<details>
<summary>✅ Správná odpověď</summary>
b) `==` (jeden `=` je přiřazení, dva `==` je porovnání)
</details>

**12. Co vrátí `range(5)`?**
- a) `[0, 1, 2, 3, 4]`
- b) `[1, 2, 3, 4, 5]`
- c) Čísla od 0 do 4 (ne seznam, ale speciální objekt)
- d) `5`

<details>
<summary>✅ Správná odpověď</summary>
c) Čísla od 0 do 4 (range vrací speciální objekt, ne seznam)
</details>

### Část B: Najděte chybu v kódu

**13. Co je špatně?**
```python
for i in range(5)
    print(i)
```

<details>
<summary>✅ Správná odpověď</summary>
Chybí dvojtečka za `range(5)` → správně: `for i in range(5):`
</details>

**14. Co je špatně?**
```python
if temperature > 38:
print("Horečka")
```

<details>
<summary>✅ Správná odpověď</summary>
Špatné odsazení! Správně:
```python
if temperature > 38:
    print("Horečka")  # 4 mezery/tab
```
</details>

**15. Co je špatně?**
```python
temps = [36.6, 37.2, 38.1]
print(temps[3])
```

<details>
<summary>✅ Správná odpověď</summary>
Index 3 neexistuje! Seznam má indexy 0, 1, 2. → `IndexError: list index out of range`
</details>

**16. Co je špatně?**
```python
result = "Věk: " + 25
```

<details>
<summary>✅ Správná odpověď</summary>
Nelze sčítat text a číslo! → `TypeError`. Správně: `result = f"Věk: {25}"` nebo `"Věk: " + str(25)`
</details>

**17. Co je špatně?**
```python
temperatures = [36.6, 37.2, 38.1]
for temp in temperature:
    print(temp)
```

<details>
<summary>✅ Správná odpověď</summary>
Překlep v názvu! Je `temperatures` (množné číslo), ale v cyklu `temperature` (jednotné). → `NameError`
</details>

### Část C: Praktické úkoly

**18. Co vypíše tento program?**
```python
count = 0
for num in [1, 2, 3, 4, 5]:
    if num % 2 == 0:
        count += 1
print(count)
```

<details>
<summary>✅ Správná odpověď</summary>
`2` (počet sudých čísel: 2, 4)
</details>

**19. Co vypíše tento kód?**
```python
for temp in [36.5, 38.5, 37.0]:
    if temp >= 38.0:
        print("Horečka")
    else:
        print("Normální")
```

<details>
<summary>✅ Správná odpověď</summary>
```
Normální
Horečka
Normální
```
</details>

**20. Co vypíše tento program?**
```python
x = 10
if x > 5 and x < 15:
    print("Ano")
else:
    print("Ne")
```

<details>
<summary>✅ Správná odpověď</summary>
`Ano` (10 je větší než 5 A zároveň menší než 15, obě podmínky platí)
</details>

**21. Co vypíše tento program?**
```python
for i in range(3):
    print(f"Řádek {i}")
```

<details>
<summary>✅ Správná odpověď</summary>
```
Řádek 0
Řádek 1
Řádek 2
```
(range(3) generuje 0, 1, 2)
</details>

**22. Co vypíše tento kód?**
```python
temp = 37.5
if temp >= 39.0:
    print("A")
else:
    if temp >= 38.0:
        print("B")
    else:
        print("C")
```

<details>
<summary>✅ Správná odpověď</summary>
`C` (37.5 není >= 39.0 ani >= 38.0, takže se provede vnořené `else`)
</details>

**23. Doplňte chybějící kód:**

```python
# Vypočítejte BMI (váha / výška²)
weight = 75  # kg
height = 1.80  # m

bmi = ___  # DOPLŇTE

if ___:  # DOPLŇTE podmínku pro BMI >= 25
    print("Nadváha")
else:
    print("Normální")
```

<details>
<summary>✅ Správná odpověď</summary>

```python
bmi = weight / (height ** 2)

if bmi >= 25:
    print("Nadváha")
else:
    print("Normální")
```

</details>

**24. Napište kód, který spočítá, kolik je v seznamu hodnot větších než 5**

```python
numbers = [3, 7, 2, 9, 5, 8]
# VÁŠ KÓD ZDE
```

<details>
<summary>✅ Správná odpověď</summary>
```python
numbers = [3, 7, 2, 9, 5, 8]
count = 0
for num in numbers:
    if num > 5:
        count += 1
print(count)  # Vypíše: 3 (čísla 7, 9, 8)
```
</details>

**25. Co udělá `x += 5`?**
- a) Nastaví x na 5
- b) Přičte 5 k x
- c) Vynásobí x pěti
- d) Porovná x s 5

<details>
<summary>✅ Správná odpověď</summary>
b) Přičte 5 k x (je to zkratka pro `x = x + 5`)
</details>

**26. Jak vypíšete všechny prvky seznamu pomocí cyklu?**
```python
fruits = ["jablko", "hruška", "banán"]
# Vyber správný kód:
```
- a) `for i in range(fruits):`
- b) `for fruit in fruits:`
- c) `for fruits in fruit:`
- d) `for i = 0 to 3:`

<details>
<summary>✅ Správná odpověď</summary>
b) `for fruit in fruits:` - správná syntaxe pro průchod seznamem
</details>

**27. Co vrátí `True or False`?**
- a) `True`
- b) `False`
- c) Chybu
- d) Záleží na kontextu

<details>
<summary>✅ Správná odpověď</summary>
a) `True` (operátor `or` vrací `True`, pokud platí alespoň jedna podmínka)
</details>

**28. Co vrátí `not True`?**
- a) `True`
- b) `False`
- c) `None`
- d) 0

<details>
<summary>✅ Správná odpověď</summary>
b) `False` (operátor `not` vrací opak - negaci)
</details>

**29. Který kód správně kontroluje, zda je číslo mezi 10 a 20 (včetně)?**
- a) `if x > 10 and x < 20:`
- b) `if x >= 10 and x <= 20:`
- c) `if x = 10 or x = 20:`
- d) `if 10 < x < 20:`

<details>
<summary>✅ Správná odpověď</summary>
b) `if x >= 10 and x <= 20:` (včetně znamená >= a <=)
</details>

**30. Co se stane, když použijeme proměnnou, která neexistuje?**
```python
print(age)  # age není definována
```
- a) `SyntaxError`
- b) `NameError`
- c) `TypeError`
- d) Vypíše `None`

<details>
<summary>✅ Správná odpověď</summary>
b) `NameError: name 'age' is not defined`
</details>

### Část D: Klávesové zkratky a speciální znaky

**31. Kterou klávesovou zkratkou zakomentujete/odkomentujete kód v PyCharmu?**
- a) `Ctrl + C`
- b) `Ctrl + K`
- c) `Ctrl + /`
- d) `Alt + /`

<details>
<summary>✅ Správná odpověď</summary>
c) `Ctrl + /` (označte řádky a stiskněte pro zakomentování/odkomentování)
</details>

**32. Kterou klávesou odsadíte kód v PyCharmu?**
- a) `Enter`
- b) `Space` (4x)
- c) `Tab`
- d) `Ctrl + I`

<details>
<summary>✅ Správná odpověď</summary>
c) `Tab` (vytvoří 4 mezery, použijte `Shift + Tab` pro odsazení zpět)
</details>

**33. Na anglické klávesnici je znak `{` dostupnější než na české. Proč?**
- a) Na české klávesnici znak `{` není
- b) Na anglické stačí `Shift + [`, na české `pravý Alt + B`
- c) Není rozdíl
- d) Na anglické klávesnici je to `Ctrl + [`

<details>
<summary>✅ Správná odpověď</summary>
b) Na anglické stačí `Shift + [`, na české `pravý Alt + B` (proto programátoři preferují anglickou klávesnici)
</details>

---
