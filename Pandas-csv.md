# Pandas — Citire CSV, Selectare Coloane, Filtrare

Acest document explică bazele librăriei **pandas**: cum se citește un fișier CSV, cum se selectează coloane, cum se filtrează rânduri, și diferența dintre **`.loc`** și **`.iloc`**.

---

# 1. Citire CSV

Un fișier **CSV** (comma-separated values) e un tabel text simplu: fiecare linie e un rând, iar valorile dintr-o linie sunt separate prin virgulă.

Exemplu de conținut `date.csv`:

```
nume,salariu,oras
Ana,3000,Cluj
Bogdan,4500,Zalau
Carmen,3800,Cluj
```

Citirea fișierului:

```python
import pandas as pd

df = pd.read_csv('date.csv')          # citește fișierul într-un DataFrame
print(df.head())                       # primele 5 rânduri
print(df.columns)                      # lista coloanelor
```

---

## Ce este o coloană

O coloană corespunde unui "câmp" din CSV — aceeași informație, repetată pe toate rândurile (ex: coloana `salariu` conține salariul fiecărei persoane).

* Toate valorile dintr-o coloană au, de regulă, același tip de date (text, număr etc.)
* Într-un DataFrame, o coloană este de tip **Series**.

## Ce este un rând

Un rând corespunde unei înregistrări/unui caz din CSV (ex: o persoană, o tranzacție).

* Un rând poate avea valori de tipuri diferite (text, număr) pe coloane diferite.
* Fiecare rând are un **index** (eticheta lui) — implicit `0, 1, 2...` dacă nu e specificat altul.

---

# 2. Selectare Coloane

```python
nume = df['nume']                      # o coloană -> Series
subset = df[['nume', 'salariu']]       # mai multe coloane -> DataFrame (atenție: listă de liste!)
```

---

# 3. Filtrare (Selectare Rânduri După o Condiție)

**Cum funcționează:** `df['coloana'] > valoare` produce o serie de `True`/`False` (câte un rezultat pentru fiecare rând). Apoi `df[serie_boolean]` păstrează **doar** rândurile unde valoarea e `True`.

```python
df['salariu'] > 4000
```

Rezultat intermediar — un "filtru" boolean, rând cu rând:

```
0    False
1     True
2    False
```

## Filtrare Simplă

```python
cluj = df[df['oras'] == 'Cluj']        # păstrează doar rândurile cu oras == 'Cluj'
```

## Combinarea Mai Multor Condiții

Atenție: fiecare condiție trebuie pusă în paranteze!

```python
adulti_bine_platiti = df[(df['varsta'] > 18) & (df['salariu'] > 3000)]  # AND - ambele trebuie să fie True
sau = df[(df['oras'] == 'Cluj') | (df['oras'] == 'Zalau')]              # OR - cel puțin una să fie True
exclude = df[~(df['oras'] == 'Cluj')]                                    # NOT - negarea condiției (tot ce nu e Cluj)
```

## Filtrare După o Listă de Valori Posibile

```python
orase_dorite = df[df['oras'].isin(['Cluj', 'Zalau'])]
```

## Filtrare După Text (Conține un Sub-string)

```python
contine_a = df[df['nume'].str.contains('a', case=False)]
```

## Filtrare + Selectare Doar a Unor Coloane din Rezultat

```python
rezultat = df[df['salariu'] > 4000][['nume', 'salariu']]
```

## Filtrare cu `.loc` (Recomandat, Mai Explicit)

```python
rezultat = df.loc[df['salariu'] > 4000, ['nume', 'salariu']]
```

---

# 4. `.loc` vs `.iloc` — Diferența

* **`.loc`** — selectează după **ETICHETĂ** (label): numele coloanei, indexul rândului
* **`.iloc`** — selectează după **POZIȚIE** (integer location): `0, 1, 2...` ca la liste

Practic: `.loc` se uită la "numele" rândului/coloanei, `.iloc` se uită la "al câtelea" e.

```python
df = pd.DataFrame({
    'nume': ['Ana', 'Bogdan', 'Carmen'],
    'salariu': [3000, 4500, 3800]
}, index=['x', 'y', 'z'])     # index personalizat (nu 0,1,2)
```

## `.loc` — Folosește Eticheta Indexului și Numele Coloanei

```python
df.loc['y']                    # rândul cu eticheta 'y' (Bogdan)
df.loc['y', 'salariu']         # 4500
df.loc['x':'y']                # rândurile de la 'x' la 'y' INCLUSIV (capătul e inclus la loc!)
df.loc[:, 'nume']              # toate rândurile, coloana 'nume'
```

## `.iloc` — Folosește Poziția Numerică (0-Indexat), Indiferent de Etichetă

```python
df.iloc[1]                     # al doilea rând (poziția 1) -> Bogdan
df.iloc[1, 1]                  # rândul 1, coloana 1 -> 4500
df.iloc[0:2]                   # rândurile de la poziția 0 la 2 EXCLUSIV (ca la slicing normal Python)
df.iloc[:, 0]                  # toate rândurile, prima coloană
```

## Diferență Importantă la Slicing

* `df.loc['x':'y']` → include și `'y'` (capătul e inclus)
* `df.iloc[0:2]` → **NU** include poziția 2 (capătul e exclus, ca la liste/`range`)

**Regulă simplă:** dacă ai un index numeric default (`0, 1, 2...`), `df.loc[2]` și `df.iloc[2]` pot da rezultate diferite dacă rândurile au fost filtrate/reordonate, pentru că `.loc` caută eticheta `2`, iar `.iloc` caută poziția a treia, indiferent de etichetă.

---

# 5. Rezumat

* `pd.read_csv()` citește un fișier CSV într-un **DataFrame**
* O **coloană** e o Series; un **rând** e o înregistrare cu index propriu
* Selectarea coloanelor: `df['col']` (Series) sau `df[['col1', 'col2']]` (DataFrame)
* Filtrarea folosește condiții booleane: `df[conditie]`, combinate cu `&` (AND), `|` (OR), `~` (NOT)
* `.isin()` filtrează după o listă de valori; `.str.contains()` filtrează după text
* `.loc` = selectare după etichetă (capăt inclus la slicing); `.iloc` = selectare după poziție (capăt exclus la slicing)
