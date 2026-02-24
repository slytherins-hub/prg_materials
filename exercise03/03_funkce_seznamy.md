# CVIČENÍ 3: FUNKCE A SEZNAMY

Algoritmizace a programování

## ÚVOD

Vítejte u třetího cvičení! Až dosud jsme pracovali s jednotlivými hodnotami – čísly, textem. Ale v reálných aplikacích potřebujeme zpracovávat **kolekce dat**: seznamy pacientů, měření ze senzorů, DNA sekvence. A k tomu potřebujeme **seznamy** (lists) a **funkce**.

> 💡 **Připomenutí:** Seznamy jste už krátce viděli v Cvičení 1 a Cvičení 2. Nyní se do nich ponoříme do hloubky!

### Co se v tomto cvičení naučíte?

1. **Funkce:**
   - Co je funkce a proč ji používat
   - Definice funkce (`def`)
   - Parametry a návratová hodnota (`return`)
   - Rozdíl mezi funkcemi a metodami

2. **Seznamy:**
   - Vytváření a indexování
   - Metody pro práci se seznamy (`.append()`, `.extend()`, `.pop()`, `.remove()`...)
   - Vnořené seznamy (tabulky a matice)

3. **Procvičování:**
   - Funkce pracující se seznamy
   - Filtrování dat
   - Hledání maxima/minima
   - Zpracování vnořených struktur

---

## CÍL 1: FUNKCE – ZÁKLADY

### 1.1 Co je to funkce?

**Funkce** je **pojmenovaný blok kódu**, který můžeme volat opakovaně. Je to jako **recept v kuchařce** – jednou napíšeme, vícekrát použijeme.

**Proč používat funkce?**
1. **Znovupoužitelnost** – Kód píšeme jen jednou
2. **Čitelnost** – Pojmenovaná funkce vysvětluje, co dělá
3. **Testovatelnost** – Funkce lze testovat samostatně
4. **Organizace** – Velký program rozdělíme na menší celky

> 💡 **Už jsi funkce používal!** Například `print()`, `len()`, `input()`, `range()` – to všechno jsou funkce, které Python poskytuje. Nyní se naučíš vytvářet vlastní!

**Medicínský příklad – výpočet BMI:**

```python
# BEZ funkce - opakování kódu
weight_1 = 75
height_1 = 1.80
bmi_1 = weight_1 / (height_1 ** 2)
print(f"BMI pacienta 1: {bmi_1:.1f}")

weight_2 = 68
height_2 = 1.65
bmi_2 = weight_2 / (height_2 ** 2)
print(f"BMI pacienta 2: {bmi_2:.1f}")

# S FUNKCÍ - elegantní řešení
def calculate_bmi(weight, height):
    """Vypočítá BMI (Body Mass Index)."""
    return weight / (height ** 2)

bmi_1 = calculate_bmi(75, 1.80)
bmi_2 = calculate_bmi(68, 1.65)
print(f"BMI pacienta 1: {bmi_1:.1f}")
print(f"BMI pacienta 2: {bmi_2:.1f}")
```

> **Klíčový princip:** **DRY – Don't Repeat Yourself**. Pokud píšete stejný kód vícekrát, potřebujete funkci!

**Proč je duplikace kódu problém?**
1. **Chyby se násobí** – Máš bug? Musíš ho opravit na 10 místech místo na jednom
2. **Změny jsou náročné** – Chceš změnit výpočet BMI? Hledáš všechny výskyty v kódu
3. **Kód je nečitelný** – 500 řádků místo 50
4. **Těžko se testuje** – Nemůžeš otestovat "funkci", která neexistuje

> 💡 **Pravidlo:** Když kopíruješ kód potřetí, zabal ho do funkce!

### 1.2 Anatomie funkce

```python
def function_name(param1, param2):
    """
    Stručný popis toho, co funkce dělá.

    Delší vysvětlení funkce (volitelné). Zde můžeme popsat,
    jak funkce pracuje, případná omezení nebo důležité poznámky.

    Args:
        param1 (typ): Popis prvního parametru.
        param2 (typ): Popis druhého parametru.

    Returns:
        typ: Popis návratové hodnoty.
    """
    # Tělo funkce
    result = param1 + param2
    return result
```

**Části funkce:**
1. `def` – Klíčové slovo pro definici funkce
2. `function_name` – Název funkce (doporučení: malá písmena, podtržítka)
3. `(param1, param2)` – Parametry (vstupy funkce)
4. `:` – Dvojtečka začínající blok funkce
5. `"""Docstring"""` – Dokumentace funkce psaná hned pod hlavičkou.
   * První řádek: stručné shrnutí funkce.
   * Prázdný řádek.
   * Detailnější popis (volitelné).
   * Sekce `Args:` – popis parametrů.
   * Sekce `Returns:` – popis návratové hodnoty.
6. Tělo funkce – Kód, který se vykoná
7. `return` – Návratová hodnota (výstup funkce)

---

### 1.3 První funkce

```python
def greet():
    """Vypíše text 'Ahoj'."""
    print("Ahoj!")

# Volání funkce
greet()  # Vypíše: Ahoj!
```

### 1.4 Funkce s parametry

```python
def greet_patient(name):
    """Pozdraví pacienta jménem.

    Args:
        name (str): Jméno pacienta.

    Returns:
        None: Funkce nic nevrací.
    """
    print(f"Dobrý den, pane/paní {name}!")

# Volání
greet_patient("Novák")    # Dobrý den, pane/paní Novák!
greet_patient("Svobodová") # Dobrý den, pane/paní Svobodová!
```

### 1.5 Funkce s návratovou hodnotou (`return`)

```python
def calculate_bmi(weight, height):
    """Vypočítá hodnotu BMI (Body Mass Index) z hmotnosti a výšky.

    Args:
        weight (float): Hmotnost v kilogramech.
        height (float): Výška v metrech.

    Returns:
        float: Vypočítaná hodnota BMI.
    """
    bmi = weight / (height ** 2)
    return bmi

# Použití
patient_bmi = calculate_bmi(75, 1.80)
print(f"BMI: {patient_bmi:.1f}")  # BMI: 23.1
```

**Klíčový rozdíl:**
* Funkce **bez `return`** nic nevrací (technicky vrací `None`)
* Funkce **s `return`** vrací hodnotu, kterou můžeme uložit nebo použít

```python
# BEZ return - jen vypíše
def print_bmi(weight, height):
    bmi = weight / (height ** 2)
    print(f"BMI: {bmi:.1f}")

print_bmi(75, 1.80)  # Vypíše: BMI: 23.1
result = print_bmi(75, 1.80)
print(result)  # None (funkce nic nevrací)

# S return - vrací hodnotu
def calculate_bmi(weight, height):
    bmi = weight / (height ** 2)
    return bmi

result = calculate_bmi(75, 1.80)
print(f"BMI: {result:.1f}")  # BMI: 23.1
```

---

### 1.6 Funkce s více parametry

```python
def evaluate_pressure(systolic, diastolic):
    """Vyhodnotí krevní tlak na základě systolické a diastolické hodnoty.

    Args:
        systolic (int | float): Systolický krevní tlak v mmHg.
        diastolic (int | float): Diastolický krevní tlak v mmHg.

    Returns:
        str: Textové vyhodnocení krevního tlaku
        ("Normální", "Vyšší normální", "Mírná hypertenze",
        nebo "Vysoká hypertenze").
    """
    if systolic < 120 and diastolic < 80:
        return "Normální"
    elif systolic < 130 and diastolic < 85:
        return "Vyšší normální"
    elif systolic < 140 and diastolic < 90:
        return "Mírná hypertenze"
    else:
        return "Vysoká hypertenze"

# Použití
result = evaluate_pressure(125, 82)
print(f"Tlak 125/82: {result}")  # Vyšší normální

result2 = evaluate_pressure(145, 95)
print(f"Tlak 145/95: {result2}")  # Vysoká hypertenze
```

---

### 1.7 📚 Doporučený postup pro začátečníky

**Nejdřív vytvoř fungující skript, pak ho zabal do funkce!**

#### Nejprve: Napiš skript s konkrétními hodnotami

```python
# Krok za krokem testuj v interaktivním režimu nebo po částech
weight = 75
height = 1.80

print(f"Váha: {weight} kg")  # Zkontroluj, že máš správnou hodnotu
print(f"Výška: {height} m")  # Zkontroluj výšku

bmi = weight / (height ** 2)
print(f"BMI: {bmi}")  # Vypočítej a zkontroluj BMI

rounded_bmi = round(bmi, 1)
print(f"BMI zaokrouhlené: {rounded_bmi}")  # Finální výsledek
```

> 💡 **Tip:** Spouštěj kód po každém řádku nebo po malých blocích – hned vidíš, co funguje a co ne!

#### Potom: Když skript funguje, zabal ho do funkce

```python
def calculate_bmi(weight, height):
    """Vypočítá BMI a vrátí jej zaokrouhlené na jedno desetinné místo.

    Args:
        weight (float): Hmotnost v kilogramech.
        height (float): Výška v metrech.

    Returns:
        float: Hodnota BMI zaokrouhlená na jedno desetinné místo.
    """
    # Zkopíruj fungující kód ze skriptu
    bmi = weight / (height ** 2)
    rounded_bmi = round(bmi, 1)
    return rounded_bmi

# Testuj funkci se stejnými hodnotami jako měl skript
result = calculate_bmi(75, 1.80)
print(f"BMI: {result}")  # Mělo by dát stejný výsledek jako skript
```

> ⚠️ **Nedělej to naopak!** Začátečníci často píšou funkci hned a pak neví, proč nefunguje. **Nejdřív rozchodíš skript, pak vytvoříš funkci.**

---

**📝 ÚKOL: První vlastní funkce**

Vytvoř program `medical_functions.py` skládající se ze tří části:

**Část 1: Pozdrav pacienta**
* Napiš funkci `greet_patient()`:
  * Funkce přijímá jeden parametr typu `str` představující jméno pacienta.
  * Funkce zobrazí personalizovaný pozdrav pacienta na základě zadaného jména.
  * Funkce nic nevrací (`None`), pouze vypíše pozdrav ve tvaru:
  ```python
  greet_patient("Jan Novák")
  # Dobrý den, pane/paní Jan Novák!
  ```

**Část 2: Validace teploty**
* Napiš funkci `has_fever()`:
  * Funkce přijímá jeden parametr typu `float` představující teplotu těla v °C.
  * Funkce vyhodnotí, zda má pacient horečku na základě zadané tělesné teploty.
  * Funkce vrátí hodnotu typu bool:
    * Vrátí `True`, pokud je teplota vyšší nebo rovna 38.0°C.
    * Vrátí `False`, pokud je teplota nižší než 38.0°C.

**Část 3: Převod teploty**
* Napiš funkci `celsius_to_fahrenheit()`:
  * Funkce přijímá jeden parametr typu `float` představující teplotu ve °C.
  * Funkce převede °C na °F (F = C × 9/5 + 32).
  * Funkce vrací hodnotu typu `float`.
  ```python
  temp_f = celsius_to_fahrenheit(36.5)
  print(f"36.5°C = {temp_f:.1f}°F")  
  # 36.5°C = 97.7°F
  ```

---

## CÍL 2: SEZNAMY

### 2.1 Co je to seznam?

**Seznam** (anglicky *list*) je **uspořádaná kolekce prvků**. Může obsahovat různé datové typy: čísla, texty, logické hodnoty, dokonce i další seznamy.

**Klíčové vlastnosti:**
* ✅ **Uspořádaný:** Prvky mají definované pořadí (index)
* ✅ **Měnitelný** (mutable): Lze přidávat, odebírat a měnit prvky – **na rozdíl od řetězců!**
* ✅ **Indexovatelný:** Přístup k prvkům přes index (od 0)
* ✅ **Heterogenní:** Může obsahovat různé datové typy

```python
# Prázdný seznam
empty_list = []
also_empty = list()

# Seznam čísel
temperatures = [36.5, 37.0, 38.2, 36.8]

# Seznam textových řetězců
patients = ["Jan Novák", "Marie Svobodová", "Petr Dvořák"]

# Seznam různých typů (heterogenní)
patient_data = ["Jan Novák", 45, True, 175.5]  # jméno, věk, pojištěn, výška
```

> 💡 **Rozdíl mezi seznamy a řetězci:** Řetězce jsou **immutable** (neměnitelné) – nemůžeš změnit jednotlivý znak. Seznamy jsou **mutable** – můžeš měnit prvky, přidávat nové, odebírat staré.

### 2.2 Vytváření seznamů

#### Přímé přiřazení

```python
numbers = [1, 2, 3, 4, 5]
names = ["Alice", "Bob", "Charlie"]
```

#### Prázdný seznam a postupné plnění

```python
measurements = []
measurements.append(36.5)
measurements.append(37.0)
measurements.append(38.2)
print(measurements)  # [36.5, 37.0, 38.2]
```

> 💡 **In-place modifikace:** `.append()` mění seznam **přímo** (in-place), protože seznamy jsou **mutable**. To je rozdíl oproti řetězcům:
> ```python
> # Seznam - MUTABLE (měnitelný)
> temps = [36.5]
> temps.append(37.0)  # Mění přímo seznam temps
> print(temps)  # [36.5, 37.0]
> 
> # Řetězec - IMMUTABLE (neměnitelný)
> text = "Ahoj"
> text.upper()  # VYTVOŘÍ nový řetězec, ale NEZMĚNÍ původní
> print(text)  # "Ahoj" (pořád malé!)
> 
> # Pro řetězce musíš přiřadit novou hodnotu:
> text = text.upper()  # Teď text obsahuje "AHOJ"
> 
> # Další metoda na stringu funguje stejně:
> word = "kocka"
> word.replace("k", "p")  # vrátí nový string, původní se nezmění
> print(word)  # "kocka"
> ```

> ⚠️ **Pozor na „kopii“ seznamu (častý zdroj skrytých chyb):**
> ```python
> a = [1, 2, 3]
> b = a        # NENÍ copied, jen druhý název pro stejný seznam
> b.append(4)
> print(a)  # [1, 2, 3, 4]
> print(b)  # [1, 2, 3, 4]
> ```
> Proč? V Pythonu proměnná drží **odkaz na objekt**. Při `b = a` nevzniká nový seznam.
>
> Pokud chceš skutečně nový (samostatný) seznam:
> ```python
> a = [1, 2, 3]
> b = a.copy()   # nebo a[:]
> b.append(4)
> print(a)  # [1, 2, 3]
> print(b)  # [1, 2, 3, 4]
> ```
> Není nutné to teď umět používat všude, ale je dobré vědět, že tohle chování může dělat těžko odhalitelné chyby.

#### Převod z jiných datových typů

```python
# Z textového řetězce
dna = list("ACGTTAGC")
print(dna)  # ['A', 'C', 'G', 'T', 'T', 'A', 'G', 'C']

# Ze stringu pomocí split()
data = "Jan,25,Praha"
parts = data.split(",")
print(parts)  # ['Jan', '25', 'Praha']
```

---

### 2.3 Indexování a slicing

Stejně jako u textových řetězců, můžeme přistupovat k jednotlivým prvkům nebo jejich částem:

```python
patients = ["Jan", "Marie", "Petr", "Anna", "Tomáš"]

# Indexování (číslování od 0)
print(patients[0])    # Jan (první prvek)
print(patients[2])    # Petr (třetí prvek)
print(patients[-1])   # Tomáš (poslední prvek)
print(patients[-2])   # Anna (předposlední)

# Slicing (výběr části)
print(patients[1:4])   # ['Marie', 'Petr', 'Anna'] (indexy 1, 2, 3)
print(patients[:3])    # ['Jan', 'Marie', 'Petr'] (od začátku do indexu 3)
print(patients[2:])    # ['Petr', 'Anna', 'Tomáš'] (od indexu 2 do konce)
print(patients[::2])   # ['Jan', 'Petr', 'Tomáš'] (každý druhý)
print(patients[::-1])  # ['Tomáš', 'Anna', 'Petr', 'Marie', 'Jan'] (pozpátku)
```

**Vizualizace indexování:**
```
Index:     0      1        2       3       4
         ┌─────┬────────┬───────┬───────┬────────┐
Pacienti:│ Jan │ Marie  │ Petr  │ Anna  │ Tomáš  │
         └─────┴────────┴───────┴───────┴────────┘
Zpětný:   -5     -4       -3      -2      -1
```

#### Změna prvku v seznamu vs řetězec (důležité)

```python
patients = ["Jan", "Marie", "Petr"]
patients[1] = "Pavel"  # OK: list je mutable
print(patients)  # ['Jan', 'Pavel', 'Petr']

word = "Marie"
# word[1] = "a"  # TypeError: 'str' object does not support item assignment
word = word.replace("a", "A")  # Správně: vytvoříš nový string
print(word)  # MArie
```

> ⚠️ **Zapamatuj si:** U seznamu můžeš změnit prvek přes index. U řetězce tohle nejde.

---

### 2.4 Operace se seznamy

#### Spojování seznamů (`+`)

```python
group_a = ["Jan", "Marie"]
group_b = ["Petr", "Anna"]
all_patients = group_a + group_b
print(all_patients)  # ['Jan', 'Marie', 'Petr', 'Anna']
```

#### Opakování (`*`)

```python
baseline = [0]
week_data = baseline * 7
print(week_data)  # [0, 0, 0, 0, 0, 0, 0]
```

#### Kontrola obsahu (`in`, `not in`)

```python
patients = ["Jan Novák", "Marie Svobodová", "Petr Dvořák"]

if "Jan Novák" in patients:
    print("Pacient je v databázi")

if "Anna Černá" not in patients:
    print("Pacient NENÍ v databázi")
```

#### Porovnávání seznamů

```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = [3, 2, 1]

print(list1 == list2)  # True (stejné prvky ve stejném pořadí)
print(list1 == list3)  # False (jiné pořadí)
```

#### Práce s více seznamy současně

**`enumerate()` – Průchod seznamem s indexem:**

```python
patients = ["Jan Novák", "Marie Svobodová", "Petr Dvořák"]

# Místo počítání indexu ručně:
for i in range(len(patients)):
    print(f"{i+1}. {patients[i]}")

# Použij enumerate() - elegantnější:
for i, patient in enumerate(patients, start=1):  # 1 = začíná od 1
    print(f"{i}. {patient}")

# Výstup:
# 1. Jan Novák
# 2. Marie Svobodová
# 3. Petr Dvořák
```

**`zip()` – Spojování dvou seznamů:**

```python
names = ["Jan", "Marie", "Petr"]
temperatures = [36.5, 37.2, 38.1]

# Projdi obě seznamy paralelně:
for name, temperature in zip(names, temperatures):
    print(f"{name}: {temperature}°C")

# Výstup:
# Jan: 36.5°C
# Marie: 37.2°C
# Petr: 38.1°C
```

> 💡 **Tip:** `zip()` funguje i pro 3 a více seznamů - např. `zip(names, temperatures, pressures)`

---

**📝 ÚKOL:** Práce se seznamy

Vytvoř program `blood_pressure.py`, který analyzuje týdenní měření krevního tlaku.

```python
# Seznam měření systolického tlaku za týden
blood_pressure = [120, 125, 118, 130, 135, 128, 122]
```

**Tvé úkoly:**
1. Najdi nejvyšší a nejnižší hodnotu měření (použij `max()` a `min()`)
2. Spočítej, kolik měření bylo nad 130 mmHg (použij `for` cyklus)
3. Vypiš všechny výsledky přehledně (použij f-stringy)
4. Vytvoř seznam dnů `days = ["Po", "Út", "St", "Čt", "Pá", "So", "Ne"]` a pomocí `zip(days, blood_pressure)` vypiš měření ve formátu `Po: 120 mmHg`

---

### 2.5 Rozdíl mezi funkcemi a metodami

```python
# FUNKCE - volá se samostatně
numbers = [3, 1, 4, 1, 5]
length = len(numbers)        # len() je funkce
maximum = max(numbers)      # max() je funkce

# METODA - volá se přes tečkovou notaci
numbers.append(9)           # append() je metoda objektu numbers
numbers.sort()              # sort() je metoda objektu numbers
```

### 2.6 Základní metody pro přidávání prvků

#### `append()` – Přidá jeden prvek na konec

```python
patients = ["Jan", "Marie"]
patients.append("Petr")
print(patients)  # ['Jan', 'Marie', 'Petr']
```

#### `extend()` – Přidá více prvků (rozbalí iterovatelný objekt)

```python
patients = ["Jan", "Marie"]
new_patients = ["Petr", "Anna"]
patients.extend(new_patients)
print(patients)  # ['Jan', 'Marie', 'Petr', 'Anna']
```

**Pozor na rozdíl mezi append() a extend():**

```python
patients = ["Jan", "Marie"]

# append() - přidá CELÝ seznam jako JEDEN item
patients.append(["Petr", "Anna"])
print(patients)  # ['Jan', 'Marie', ['Petr', 'Anna']] ← vnořený seznam!

# extend() - rozbalí seznam a přidá jednotlivé prvky
patients2 = ["Jan", "Marie"]
patients2.extend(["Petr", "Anna"])
print(patients2)  # ['Jan', 'Marie', 'Petr', 'Anna']
```

#### `insert()` – Vloží prvek na konkrétní pozici

```python
patients = ["Jan", "Marie", "Petr"]
patients.insert(1, "Anna")  # Vlož na index 1
print(patients)  # ['Jan', 'Anna', 'Marie', 'Petr']
```

**💻 Příklad: Fronta pacientů v čekárně**

```python
# Prázdná fronta
waiting_room = []

# Příchod pacientů
waiting_room.append("Jan Novák")
waiting_room.append("Marie Svobodová")
waiting_room.append("Petr Dvořák")
print("Fronta:", waiting_room)

# Urgentní případ - přednost
waiting_room.insert(0, "Anna Nová - URGENTNÍ")
print("Po urgenci:", waiting_room)
```

---

### 2.7 Metody pro odebírání prvků

#### `remove()` – Odebere první výskyt zadaného prvku

```python
patients = ["Jan", "Marie", "Petr", "Marie"]
patients.remove("Marie")  # Odebere první "Marie"
print(patients)  # ['Jan', 'Petr', 'Marie']
```

⚠️ **Pozor:** Pokud prvek neexistuje, nastane chyba `ValueError`!

```python
patients = ["Jan", "Marie"]
# patients.remove("Anna")  # ValueError: list.remove(x): x not in list

# Bezpečnější varianta s kontrolou
if "Anna" in patients:
    patients.remove("Anna")
else:
    print("Pacient není v seznamu")
```

#### `pop()` – Odebere a vrátí prvek na indexu (výchozí: poslední)

```python
patients = ["Jan", "Marie", "Petr", "Anna"]

# Bez argumentu - odebere poslední
last = patients.pop()
print(last)      # Anna
print(patients)  # ['Jan', 'Marie', 'Petr']

# S indexem - odebere item na indexu
first = patients.pop(0)
print(first)     # Jan
print(patients)  # ['Marie', 'Petr']
```

**💻 Příklad: Správa fronty pacientů**

```python
queue = ["Jan Novák", "Marie Svobodová", "Petr Dvořák", "Anna Černá"]
print("Původní fronta:", queue)

# Zavolání prvního pacienta
current_patient = queue.pop(0)
print(f"\nVoláme pacienta: {current_patient}")
print("Zbývá ve frontě:", queue)

# Pacient Marie Svobodová odchází (zrušila návštěvu)
queue.remove("Marie Svobodová")
print("Po zrušení:", queue)

# Příchod nového pacienta
queue.append("Tomáš Novotný")
print("Po příchodu nového:", queue)
```

---

### 2.8 Další užitečné metody

#### `index()` – Najde index prvního výskytu prvku

```python
patients = ["Jan", "Marie", "Petr", "Anna"]
position = patients.index("Petr")
print(position)  # 2
```

#### `count()` – Spočítá výskyty prvku

```python
measurements = [36.5, 37.0, 36.5, 38.0, 36.5]
count_normal = measurements.count(36.5)
print(count_normal)  # 3
```

#### `sort()` – Seřadí seznam (in-place, mění původní)

```python
numbers = [5, 2, 8, 1, 9]
numbers.sort()
print(numbers)  # [1, 2, 5, 8, 9]

# Sestupně
numbers.sort(reverse=True)
print(numbers)  # [9, 8, 5, 2, 1]
```

⚠️ **Pozor:** `sort()` nemá návratovou hodnotu (vrací `None`), mění seznam na místě!

```python
numbers = [5, 2, 8]
result = numbers.sort()
print(result)    # None ← metoda nevrací hodnotu
print(numbers)   # [2, 5, 8] ← seznam je změněný
```

**Alternativa – funkce `sorted()`** (vrací nový seznam):

```python
numbers = [5, 2, 8]
sorted_numbers = sorted(numbers)
print(numbers)         # [5, 2, 8] ← původní nezměněn
print(sorted_numbers)  # [2, 5, 8] ← nový seřazený
```

> 💡 **Kdy použít co?** `list.sort()` - když chceš seřadit původní seznam (úspora paměti). `sorted(list)` - když potřebuješ zachovat i původní seznam.


**📝 ÚKOL:** Práce s metodami seznamů

Vytvoř program `patient_list.py`, který simuluje správu seznamu pacientů v ordinaci.

**Tvé úkoly:**
1. Vytvoř prázdný seznam `patients`.
2. Přidej postupně 5 pacientů pomocí `append()`: Jan Novák, Marie Svobodová, Petr Dvořák, Anna Černá, Tomáš Novotný.
3. Vypiš aktuální stav seznamu.
4. Odeber prvního pacienta (byl ošetřen) pomocí `pop(0)` a vypiš ho.
5. Pacient "Petr Dvořák" zrušil návštěvu - odeber ho pomocí `remove()`.
6. Přidej na začátek urgentního pacienta "Karel Urgentní" pomocí `insert(0, ...)`.
7. Seřaď zbývající pacienty abecedně pomocí `sort()`.
8. Vypiš konečný stav seznamu.

**Očekávaný výstup:**
```
Původní seznam: ['Jan Novák', 'Marie Svobodová', 'Petr Dvořák', 'Anna Černá', 'Tomáš Novotný']
Ošetřen: Jan Novák
Po ošetření: ['Marie Svobodová', 'Petr Dvořák', 'Anna Černá', 'Tomáš Novotný']
Po zrušení: ['Marie Svobodová', 'Anna Černá', 'Tomáš Novotný']
Po urgenci: ['Karel Urgentní', 'Marie Svobodová', 'Anna Černá', 'Tomáš Novotný']
Seřazeno: ['Anna Černá', 'Karel Urgentní', 'Marie Svobodová', 'Tomáš Novotný']
```

---

### 2.9 Co jsou vnořené seznamy?

**Vnořený seznam** je seznam, jehož prvky jsou také seznamy. Používá se např. pro reprezentaci **dvourozměrných dat** (tabulky, matice).

```python
# Tabulka pacientů: [jméno, věk, temperature]
patients_data = [
    ["Jan Novák", 45, 36.5],
    ["Marie Svobodová", 32, 37.2],
    ["Petr Dvořák", 28, 38.1]
]
```

**Proč používat vnořené seznamy?**
* Reprezentace **tabulek** (řádky a sloupce)
* **Matice** v matematice a obrazovém zpracování
* **Vícerozměrná data** (např. týdenní měření více pacientů)

---

### 2.10 Indexování vnořených seznamů

Používáme **vícenásobné indexování**: `list[row][column]`

```python
# Tabulka pacientů
patients = [
    ["Jan Novák", 45, 36.5],      # Index 0
    ["Marie Svobodová", 32, 37.2], # Index 1
    ["Petr Dvořák", 28, 38.1]      # Index 2
]

# Přístup k celému řádku
print(patients[0])  # ['Jan Novák', 45, 36.5]

# Přístup ke konkrétnímu prvku
print(patients[0][0])  # Jan Novák (první pacient, jméno)
print(patients[0][1])  # 45 (první pacient, věk)
print(patients[0][2])  # 36.5 (první pacient, temperature)

print(patients[1][0])  # Marie Svobodová (druhý pacient, jméno)
print(patients[2][2])  # 38.1 (třetí pacient, temperature)
```

**Vizualizace indexování:**

```
         [0]              [1]   [2]
    ┌────────────────┬──────┬───────┐
[0] │ "Jan Novák"    │  45  │ 36.5  │
    ├────────────────┼──────┼───────┤
[1] │ "Marie Svobod."│  32  │ 37.2  │
    ├────────────────┼──────┼───────┤
[2] │ "Petr Dvořák"  │  28  │ 38.1  │
    └────────────────┴──────┴───────┘

Přístup: patients[řádek][sloupec]
Příklad: patients[1][2] = 37.2
```

---

### 2.11 Iterace přes vnořené seznamy

#### Cyklus přes řádky

```python
patients = [
    ["Jan Novák", 45, 36.5],
    ["Marie Svobodová", 32, 37.2],
    ["Petr Dvořák", 28, 38.1]
]

# Zpracování každého pacienta
for patient in patients:
    name = patient[0]
    age = patient[1]
    temperature = patient[2]
    print(f"{name} ({age} let): {temperature}°C")
```

**Výstup:**
```
Jan Novák (45 let): 36.5°C
Marie Svobodová (32 let): 37.2°C
Petr Dvořák (28 let): 38.1°C
```

#### Vnořený cyklus (řádky × sloupce)

```python
# Matice 3×3
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Projdi všechny prvky
for row in matrix:
    for item in row:
        print(item, end=" ")
    print()  # Nový řádek po každém řádku matrix
```

**Výstup:**
```
1 2 3 
4 5 6 
7 8 9 
```

> 💡 **Jak vnořený cyklus funguje (krokování):**
> 1. Vnější cyklus vezme první řádek `[1, 2, 3]`
>    * Vnitřní cyklus projde: `item=1` → vypíše "1 ", `item=2` → vypíše "2 ", `item=3` → vypíše "3 "
>    * Po vnitřním cyklu: `print()` → nový řádek
> 2. Vnější cyklus vezme druhý řádek `[4, 5, 6]`
>    * Vnitřní cyklus projde: `item=4` → vypíše "4 ", `item=5` → vypíše "5 ", `item=6` → vypíše "6 "
>    * Po vnitřním cyklu: `print()` → nový řádek
> 3. Vnější cyklus vezme třetí řádek `[7, 8, 9]`
>    * Vnitřní cyklus projde: `item=7` → vypíše "7 ", `item=8` → vypíše "8 ", `item=9` → vypíše "9 "
>    * Po vnitřním cyklu: `print()` → nový řádek
>
> **Tip:** Zkus si tento kód prokrokovat v debuggeru PyCharm – uvidíš, jak se proměnné mění krok po kroku!

---

### 2.12 Vytváření vnořených seznamů

#### Přímé vytvoření

```python
measurements = [
    ["Pondělí", 36.5, 120, 80],
    ["Úterý", 36.7, 125, 82],
    ["Středa", 37.2, 128, 85]
]
```

#### Postupné plnění

```python
# Prázdná tabulka
weekly_data = []

# Přidávání řádků
weekly_data.append(["Pondělí", 36.5])
weekly_data.append(["Úterý", 36.7])
weekly_data.append(["Středa", 37.2])

print(weekly_data)
# [['Pondělí', 36.5], ['Úterý', 36.7], ['Středa', 37.2]]
```

#### Pomocí cyklu

```python
# Vytvoř matici 3×3 plnou nul
matrix = []
for i in range(3):
    row = []
    for j in range(3):
        row.append(0)
    matrix.append(row)

print(matrix)
# [[0, 0, 0], [0, 0, 0], [0, 0, 0]]

# Nebo jednodušeji s násobením
matrix = []
for i in range(3):
    matrix.append([0] * 3)
```

> ⚠️ **Krátká poznámka k vnořeným seznamům:**  
> `list.copy()` dělá jen **mělkou kopii** (zkopíruje vnější seznam, ne vnitřní seznamy).  
> U vnořených struktur pak můžeš nechtěně měnit data i v „kopii“.  
> Když potřebuješ opravdu nezávislou kopii celé vnořené struktury, existuje `copy.deepcopy(...)` (z modulu `copy`).
> 
> ```python
> import copy
> 
> original = [[1, 2], [3, 4]]
> copied = copy.deepcopy(original)
> copied[0][0] = 99
> 
> print(original)  # [[1, 2], [3, 4]]
> print(copied)    # [[99, 2], [3, 4]]
> ```

---

**📝 ÚKOL: Analýza teplot pacientů**

Vytvoř program `temperature_analysis.py`, který zpracuje teplotní záznamy pacientů.

**Vstupní data:**

```python
# Data: [jméno, teplota_den1, teplota_den2, teplota_den3]
temperature_log = [
        ["Jan Novák", 36.5, 36.7, 36.6],
        ["Marie Svobodová", 37.2, 38.1, 38.5],
        ["Petr Dvořák", 36.8, 36.9, 37.0]
]
```

**Tvé úkoly:**
1. Projdi všechny pacienty pomocí `for` cyklu.
2. U každého pacienta spočítej průměrnou teplotu (`sum(...) / len(...)`).
3. U každého pacienta najdi maximální naměřenou teplotu (`max(...)`).
4. Vypiš výstup ve formátu:
   * `Jméno pacienta: ...`
   * `Průměr: ...°C`
   * `Maximum: ...°C`
5. Pokud je maximální teplota vyšší nebo rovna 38.0°C, vypiš navíc varování:
   * `POZOR: Byla zaznamenána horečka!`

---

## CÍL 3: PROCVIČOVÁNÍ

Nyní spojíme vše dohromady – seznamy, cykly, podmínky a funkce.

### 3.1 Filtrování seznamu pomocí funkce

```python
def has_fever(temperature):
    """Kontroluje, zda daná teplota znamená horečku."""
    return temperature >= 38.0

# Seznam měření
temperatures = [36.5, 37.2, 38.1, 36.8, 38.5, 37.0, 39.0]

# Filtrování - najdi všechny horečky
fevers = []
for temp in temperatures:
    if has_fever(temp):
        fevers.append(temp)

print(f"Horečky: {fevers}")
print(f"Počet horečnatých měření: {len(fevers)}")
```

---

**📝 ÚKOL: Analýza krevního tlaku**

Vytvoř program `blood_pressure_analysis.py`, který:

1. Definuje funkci `classify_pressure(systolic, diastolic)`, která vrací kategorii:
   * systolický tlak menší než 120 a zároveň diastolický tlak menší než 80: `"Normální"`,
   * systolický tlak menší než 130 a zároveň diastolický tlak menší než 85: `"Vyšší normální"`,
   * systolický tlak menší než 140 a zároveň diastolický tlak menší než 90: `"Hypertenze 1. stupně"`,
   * jinak: `"Hypertenze 2. stupně"`.

2. Vytvoří seznam měření šesti pacientů:
   ```python
   measurements = [
       ["Jan", 118, 78],
       ["Marie", 135, 88],
       ["Petr", 125, 82],
       ["Anna", 145, 95],
       ["Tomáš", 119, 79],
       ["Eva", 142, 91]
   ]
   ```

3. Projde všechna měření a:
   * Vypíše jméno, hodnoty a kategorii.
   * Spočítá, kolik pacientů má hypertenzi (1. nebo 2. stupně).
   * Najde pacienta s nejvyšším systolickým tlakem.

**Očekávaný výstup:**
```
=== ANALÝZA KREVNÍHO TLAKU ===
Jan: 118/78 mmHg → Normální
Marie: 135/88 mmHg → Hypertenze 1. stupně
Petr: 125/82 mmHg → Vyšší normální
Anna: 145/95 mmHg → Hypertenze 2. stupně
Tomáš: 119/79 mmHg → Normální
Eva: 142/91 mmHg → Hypertenze 2. stupně

STATISTIKA:
Pacientů s hypertenzí: 3
Nejvyšší tlak: Anna (145/95 mmHg)
```

---

**📝 ÚKOL: Statistika DNA sekvence s funkcemi**

Vytvoř program pro komplexní analýzu DNA sekvence s využitím funkcí.

1. Vytvoř funkci `analyze_dna()`:
   * Funkce přijímá jeden parametr typu `str` (DNA sekvence, např. `"ACGTTAGCTA"`).
   * Funkce spočítá počet jednotlivých nukleotidů (A, C, G, T)
   * Funkce vypočítá GC obsah v procentech: `(počet_G + počet_C) / celková_délka * 100`
   * Funkce vrátí hodnotu typu `list` s vypočítanými hodnotami v pořadí: *počet A, počet C, počet G, počet T, GC procenta*.

2. Vytvoř funkci `find_motifs()`:
   * Funkce přijímá dva parametry typu `str`:
     * DNA sekvenci,
     * hledaný motiv (podřetězec).
   * Funkce najde všechny výskyty zadaného motivu v DNA sekvenci. Tedy vyhledá všechny pozice (indexy), kde hledaný motiv začíná.
   * Funkce vrátí hodnotu typu `list` obsahující indexy nalezených výskytů.

3. Vytvoř funkci `complementary_strand()`:
   * Funkce přijímá jeden parametr typu `str` (DNA sekvence).
   * Funkce vytvoří komplementární řetězec podle pravidel párování bází (A ↔ T, C ↔ G).
   * Funkce vrátí hodnotu typu `str` (komplementární sekvence).

4. Hlavní program:
    ```python
    dna = "ACGTTAGCTAGCTAGCTAACGTA"
   
    # Analýza
    stats = analyze_dna(dna)
    print(f"=== ANALÝZA DNA ===")
    print(f"Sekvence: {dna}")
    print(f"Délka: {len(dna)} bp")
    print(f"A: {stats[0]}, C: {stats[1]}, G: {stats[2]}, T: {stats[3]}")
    print(f"GC obsah: {stats[4]:.1f}%")
   
    # Hledání motivu
    motif = "GCT"
    positions = find_motifs(dna, motif)
    print(f"\nMotiv '{motif}' nalezen na pozicích: {positions}")
   
    # Komplementární řetězec
    complement = complementary_strand(dna)
    print(f"\nKomplementární řetězec: {complement}")
    ```

**Očekávaný výstup:**
```
=== ANALÝZA DNA ===
Sekvence: ACGTTAGCTAGCTAGCTAACGTA
Délka: 23 bp
A: 8, C: 6, G: 5, T: 4
GC obsah: 47.8%

Motiv 'GCT' nalezen na pozicích: [4, 8, 12]

Komplementární řetězec: TGCAATCGATCGATCGATTGCAT
```

---

## 🌟 BONUSOVÉ ÚKOLY

Tyto úkoly jsou pro ty, kteří chtějí procvičit nabyté znalosti nad rámec povinných úkolů.

### Správa databáze pacientů

Napište program pro správu databáze pacientů s vnořenými seznamy a funkcemi.

**Zadání:**
1. Vytvořte funkci `add_patient()`:
   * Funkce přijímá čtyři parametry:
     * databázi typu `list`,
     * jméno pacienta typu `str`,
     * věk pacienta typu `int`,
     * diagnóza typu `str`.
   * Funkce vytvoří nový seznam reprezentující pacienta a přidá ho do databáze jako nový vnořený seznam.
   * Funkce vrátí hodnotu typu `list` představující aktualizovanou databázi.

2. Vytvořte funkci `find_patients_by_diagnosis()`:
   * Funkce přijímá dva parametry:
     * databázi typu `list`,
     * diagnózu typu `str`.
   * Funkce vyhledá v databázi všechny pacienty se zadanou diagnózou bez ohledu na velikost písmen (case-insensitive).
   * Funkce vrátí:
     * hodnotu typu `list` obsahující jména pacientů s požadovanou diagnózou,
     * nebo `None`, pokud žádní pacienti s danou diagnózou nejsou.

3. Vytvořte funkci `average_age_by_diagnosis()`:
   * Funkce přijímá dva parametry:
     * databázi typu `list`,
     * diagnózu typu `str`.
   * Funkce vyhledá v databázi všechny pacienty se zadanou diagnózou a spočítá jejich průměrný věk.
   * Funkce vrátí:
     * hodnotu typu `float` představující průměrný věk,
     * nebo `None`, pokud žádní pacienti s danou diagnózou nejsou.

4. Vytvořte funkci `print_database()`:
   * Funkce přijímá databázi typu `list`.
   * Funkce přehledně vypíše všechny pacienty v databázi (použijte funkci `enumerate()` pro číslování).
   * Funkce nic nevrací (`None`), pouze vypisuje data.

5. Hlavní program:
   ```python
   # Inicializace prázdné databáze
   patients_db = []
   
   # Přidání pacientů
   patients_db = add_patient(patients_db, "Jan Novák", 45, "Diabetes")
   patients_db = add_patient(patients_db, "Marie Svobodová", 32, "Hypertenze")
   patients_db = add_patient(patients_db, "Petr Dvořák", 28, "Diabetes")
   patients_db = add_patient(patients_db, "Anna Černá", 51, "Hypertenze")
   patients_db = add_patient(patients_db, "Tomáš Novotný", 39, "Diabetes")
   
   # Výpis databáze
   print("=== DATABÁZE PACIENTŮ ===")
   print_database(patients_db)
   
   # Vyhledání podle diagnózy
   print("\n=== PACIENTI S DIABETEM ===")
   diabetic_patients = find_patients_by_diagnosis(patients_db, "diabetes")
   for name in diabetic_patients:
       print(f"- {name}")
   
   # Statistika
   print("\n=== STATISTIKA ===")
   avg_diabetes = average_age_by_diagnosis(patients_db, "diabetes")
   avg_hypertension = average_age_by_diagnosis(patients_db, "hypertenze")
   print(f"Průměrný věk pacientů s diabetem: {avg_diabetes:.1f} let")
   print(f"Průměrný věk pacientů s hypertenzí: {avg_hypertension:.1f} let")
   ```

**Očekávaný výstup:**
```
=== DATABÁZE PACIENTŮ ===
1. Jan Novák (45 let) - Diabetes
2. Marie Svobodová (32 let) - Hypertenze
3. Petr Dvořák (28 let) - Diabetes
4. Anna Černá (51 let) - Hypertenze
5. Tomáš Novotný (39 let) - Diabetes

=== PACIENTI S DIABETEM ===
- Jan Novák
- Petr Dvořák
- Tomáš Novotný

=== STATISTIKA ===
Průměrný věk pacientů s diabetem: 37.3 let
Průměrný věk pacientů s hypertenzí: 41.5 let
```

---

## 📝 SELF-CHECK: PROCVIČENÍ ZNALOSTÍ

### Část A: Funkce - základy

**1. Co vrátí tato funkce?**
```python
def calculate(x, y):
    result = x + y
    
print(calculate(5, 3))
```
- a) 8
- b) None
- c) 5
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
b) None - funkce nic nevrací (chybí `return`), takže vrací implicitně `None`
</details>

**2. Jaký je rozdíl mezi funkcí a metodou?**
- a) Žádný rozdíl
- b) Funkce se volá samostatně `len(list)`, metoda přes tečku `list.append()`
- c) Funkce jsou rychlejší
- d) Metody jsou zastaralé

<details>
<summary>✅ Správná odpověď</summary>
b) Funkce se volá samostatně (např. `len(numbers)`), metoda se volá na objektu přes tečku (např. `numbers.append(5)`)
</details>

**3. Co znamená princip DRY?**
- a) "Don't Run Yet" - nespouštěj zatím
- b) "Don't Repeat Yourself" - neopakuj se
- c) "Do Require Yield" - vyžaduj yield
- d) "Debug Right Yesterday" - debuguj hned

<details>
<summary>✅ Správná odpověď</summary>
b) "Don't Repeat Yourself" - pokud píšeš stejný kód vícekrát, zabal ho do funkce
</details>

**4. Co vypíše tento kód?**
```python
def greet(name):
    return f"Ahoj, {name}!"
    print("Konec")

result = greet("Jan")
print(result)
```
- a) Ahoj, Jan! a Konec
- b) Jen Ahoj, Jan!
- c) Jen Konec
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
b) Jen "Ahoj, Jan!" - `return` ukončí funkci, `print("Konec")` se nikdy neprovede
</details>

**5. Jaký je správný Google-style docstring?**
- a) `# Tato funkce počítá BMI`
- b) `"""Počítá BMI."""`
- c) 
```python
"""Počítá BMI.

Args:
    weight: Hmotnost v kg
    height: Výška v metrech

Returns:
    BMI jako float
"""
```
- d) `// Počítá BMI`

<details>
<summary>✅ Správná odpověď</summary>
c) Trojité uvozovky s popisem, Args a Returns sekcemi
</details>

### Část B: Seznamy - základy a operace

**6. Co je pravda o seznamech?**
- a) Jsou immutable (neměnitelné)
- b) Jsou mutable (měnitelné)
- c) Mohou obsahovat jen čísla
- d) Indexují se od 1

<details>
<summary>✅ Správná odpověď</summary>
b) Jsou mutable - můžeš měnit prvky, přidávat, odebírat (na rozdíl od stringů)
</details>

**7. Co vypíše `[1, 2, 3] + [4, 5]`?**
- a) `[1, 2, 3, 4, 5]`
- b) `[5, 7, 3]`
- c) `15`
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
a) `[1, 2, 3, 4, 5]` - operátor `+` spojuje seznamy (concatenation)
</details>

**8. Co vrátí `[10, 20, 30][1]`?**
- a) 10
- b) 20
- c) 30
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
b) 20 - index 1 je druhý prvek (indexuje se od 0)
</details>

**9. Co udělá tento kód?**
```python
numbers = [1, 2, 3]
numbers[1] = 99
```
- a) Chybu - seznamy jsou immutable
- b) Vytvoří nový seznam
- c) Změní druhý prvek na 99: `[1, 99, 3]`
- d) Přidá 99 na konec

<details>
<summary>✅ Správná odpověď</summary>
c) Změní druhý prvek na 99 - seznamy jsou mutable, prvky lze měnit
</details>

**10. Co vypíše tento kód?**
```python
names = ["Jan", "Marie", "Petr"]
for i, name in enumerate(names, 1):
    print(f"{i}. {name}")
```
- a) 0. Jan, 1. Marie, 2. Petr
- b) 1. Jan, 2. Marie, 3. Petr
- c) Jan, Marie, Petr
- d) Chybu

<details>
<summary>✅ Správná odpověď</summary>
b) 1. Jan, 2. Marie, 3. Petr - `enumerate(list, 1)` začíná číslovat od 1
</details>

### Část C: Metody seznamů

**11. Jaký je rozdíl mezi `append()` a `extend()`?**
- a) Žádný rozdíl
- b) `append()` přidá celý seznam jako jeden prvek, `extend()` přidá jednotlivé prvky
- c) `append()` je rychlejší
- d) `extend()` je zastaralé

<details>
<summary>✅ Správná odpověď</summary>
b) `numbers.append([4, 5])` → `[1, 2, 3, [4, 5]]` (vnořený), `numbers.extend([4, 5])` → `[1, 2, 3, 4, 5]` (rozbalené)
</details>

**12. Co vrátí metoda `sort()`?**
- a) Seřazený seznam
- b) None
- c) True/False
- d) Index

<details>
<summary>✅ Správná odpověď</summary>
b) None - `sort()` mění seznam na místě (in-place) a nic nevrací
</details>

**13. Co udělá `numbers.pop()`?**
- a) Odebere a vrátí první prvek
- b) Odebere a vrátí poslední prvek
- c) Odebere všechny prvky
- d) Vypíše seznam

<details>
<summary>✅ Správná odpověď</summary>
b) Odebere a vrátí poslední prvek - `pop(0)` by odebralo první
</details>

**14. Kdy použít `sorted()` místo `sort()`?**
- a) Nikdy - `sort()` je vždy lepší
- b) Když chceš zachovat původní seznam nezměněný
- c) Když chceš seřadit vzestupně
- d) Když je seznam krátký

<details>
<summary>✅ Správná odpověď</summary>
b) `sorted(list)` vrací nový seřazený seznam a původní nechává nezměněný. `list.sort()` mění původní seznam.
</details>

**15. Co se stane při `numbers.remove(5)`, když 5 není v seznamu?**
- a) Nic
- b) ValueError
- c) Vrátí None
- d) Odebere první prvek

<details>
<summary>✅ Správná odpověď</summary>
b) ValueError: list.remove(x): x not in list - proto je lepší nejdřív zkontrolovat `if 5 in numbers:`
</details>

### Část D: Vnořené seznamy

**16. Co vrátí `[[1, 2], [3, 4]][1][0]`?**
- a) 1
- b) 2
- c) 3
- d) 4

<details>
<summary>✅ Správná odpověď</summary>
c) 3 - `[1][0]` znamená: vezmi druhý řádek `[3, 4]`, z něj první prvek `3`
</details>

**17. Jak vytvoříš matici 2×3 plnou nul?**
- a) `[[0] * 2] * 3`
- b) `[[0, 0, 0], [0, 0, 0]]`
- c) `[0] * 6`
- d) `matrix(2, 3)`

<details>
<summary>✅ Správná odpověď</summary>
b) `[[0, 0, 0], [0, 0, 0]]` - varianta a) vytvoří 3 reference na STEJNÝ seznam (nebezpečné!)
</details>

**18. Co vypíše tento vnořený cyklus?**
```python
for i in range(2):
    for j in range(3):
        print(i, j, end=" ")
```
- a) 0 0 0 1 1 1 2 2 2
- b) 0 1 2 0 1 2
- c) 0 0 0 1 0 2 1 0 1 1 1 2
- d) 2 3

<details>
<summary>✅ Správná odpověď</summary>
c) 0 0 0 1 0 2 1 0 1 1 1 2 - vnější cyklus 2×, vnitřní cyklus pro každou iteraci vnějšího 3×
</details>

### Část E: Kombinace konceptů

**19. Co je špatně v tomto kódu?**
```python
def sum_list(numbers):
    for number in numbers:
        total = total + number
    return total
```
- a) Nic, je to správně
- b) `total` není inicializováno před použitím
- c) Špatná syntaxe cyklu
- d) `return` je mimo funkci

<details>
<summary>✅ Správná odpověď</summary>
b) `total` musí být nejdřív inicializováno: `total = 0` před cyklem, jinak bude UnboundLocalError
</details>

**20. Co vrátí tato funkce?**
```python
def find_maximum(numbers_list):
    max_value = numbers_list[0]
    for item in numbers_list:
        if item > max_value:
            max_value = item
    return max_value

result = find_maximum([3, 7, 2, 9, 1])
```
- a) 3
- b) 7
- c) 9
- d) [3, 7, 2, 9, 1]

<details>
<summary>✅ Správná odpověď</summary>
c) 9 - funkce najde a vrátí maximální hodnotu ze seznamu
</details>

---



