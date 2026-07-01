# Modulul `random` în Python — `random()`, `randint()`, `randrange()` și Exemple

Acest document explică cele mai folosite funcții din modulul **`random`**, folosite pentru a genera valori aleatoare.

---

# 1. Ce Este Modulul `random`?

`random` este un modul **built-in** al Python-ului, care oferă funcții pentru generarea de numere/alegeri aleatoare.

Pentru a-l folosi, trebuie importat la începutul programului:

```python
import random
```

---

# 2. `random.random()` — Număr Zecimal Aleator între 0 și 1

Sintaxă:

```python
random.random()
```

* nu primește niciun parametru
* returnează un număr **float** aleator, `0.0 <= x < 1.0`

## Exemplu 1

```python
import random

x = random.random()
print(x)
```

Output (exemplu, valoarea diferă la fiecare rulare):

```
0.6741253771221944
```

## Exemplu 2 — Generarea unui Număr Zecimal într-un Interval Oarecare

```python
import random

minim = 5
maxim = 10

numar = minim + random.random() * (maxim - minim)
print(numar)
```

Output (exemplu):

```
7.930212819417322
```

Explicație:

`random.random()` dă mereu un număr între 0 și 1; înmulțind cu lungimea intervalului și adunând `minim`, obținem un număr aleator în orice interval dorit.

## Exemplu 3 — Simularea unei Șanse/Probabilități (30%)

```python
import random

sansa = 0.3   # 30%

if random.random() < sansa:
    print("Eveniment produs!")
else:
    print("Eveniment neprodus.")
```

Output (exemplu):

```
Eveniment neprodus.
```

Explicație:

Deoarece `random.random()` returnează valori uniform distribuite între `0.0` și `1.0`, condiția `random.random() < 0.3` este adevărată în aproximativ 30% din cazuri.

## Exemplu 4 — Generarea unui Preț cu Două Zecimale

```python
import random

pret = round(random.random() * 100, 2)
print(pret)
```

Output (exemplu):

```
57.42
```

Explicație:

`round(x, 2)` rotunjește numărul la 2 zecimale, util când se generează valori de tip preț/procent.

## Exemplu 5 — Generarea a Mai Multor Numere Zecimale

```python
import random

for i in range(5):
    print(round(random.random(), 3))
```

Output (exemplu):

```
0.128
0.734
0.951
0.062
0.489
```

---

# 3. `random.randint(a, b)` — Număr Întreg Aleator, Capete Incluse

Sintaxă:

```python
random.randint(a, b)
```

* returnează un număr **întreg** aleator, `a <= x <= b`
* **ambele capete sunt incluse**

## Exemplu 1 — Zar Simulat (1-6)

```python
import random

zar = random.randint(1, 6)
print(zar)
```

Output (exemplu):

```
4
```

## Exemplu 2 — Generarea a 5 Numere între 1 și 100

```python
import random

for i in range(5):
    print(random.randint(1, 100))
```

Output (exemplu):

```
23
87
5
61
99
```

## Exemplu 3 — Numere Negative

```python
import random

x = random.randint(-10, 10)
print(x)
```

Output (exemplu):

```
-3
```

## Exemplu 4 — Simularea Aruncării unei Monede

```python
import random

moneda = random.randint(0, 1)

if moneda == 0:
    print("Cap")
else:
    print("Pajura")
```

Output (exemplu):

```
Cap
```

## Exemplu 5 — Suma a Două Zaruri

```python
import random

zar1 = random.randint(1, 6)
zar2 = random.randint(1, 6)

print("Zar 1:", zar1)
print("Zar 2:", zar2)
print("Suma:", zar1 + zar2)
```

Output (exemplu):

```
Zar 1: 3
Zar 2: 5
Suma: 8
```

## Exemplu 6 — O Listă cu 10 Numere Aleatoare între 1 și 50

```python
import random

numere = []
for i in range(10):
    numere.append(random.randint(1, 50))

print(numere)
```

Output (exemplu):

```
[12, 45, 3, 28, 50, 7, 19, 33, 41, 6]
```

## Exemplu 7 — Aceeași Listă, cu List Comprehension

```python
import random

numere = [random.randint(1, 50) for i in range(10)]
print(numere)
```

Output (exemplu):

```
[9, 44, 22, 17, 3, 50, 31, 6, 28, 14]
```

## Exemplu 8 — Notă Aleatoare pentru un Student (1-10)

```python
import random

nota = random.randint(1, 10)
print("Nota obținută:", nota)
```

Output (exemplu):

```
Nota obținută: 7
```

## Exemplu 9 — Coordonate Aleatoare (x, y) pe o Tablă 0-9

```python
import random

x = random.randint(0, 9)
y = random.randint(0, 9)

print("Poziție:", (x, y))
```

Output (exemplu):

```
Poziție: (4, 7)
```

---

# 4. `random.randrange(start, stop, pas)` — Ca `range()`, dar Alege un Element Aleator

Sintaxă:

```python
random.randrange(stop)
random.randrange(start, stop)
random.randrange(start, stop, pas)
```

* funcționează ca `range()`: **`stop` este exclus**
* dacă se dă un singur argument, se consideră `start = 0`
* al treilea argument (`pas`) este opțional

## Exemplu 1 — Un Singur Argument

```python
import random

x = random.randrange(10)     # un număr din 0, 1, 2, ..., 9
print(x)
```

Output (exemplu):

```
7
```

## Exemplu 2 — `start` și `stop`

```python
import random

x = random.randrange(5, 15)   # un număr din 5, 6, ..., 14 (15 e exclus)
print(x)
```

Output (exemplu):

```
11
```

## Exemplu 3 — Cu Pas — Doar Numere Pare

```python
import random

x = random.randrange(0, 20, 2)   # un număr din 0, 2, 4, ..., 18
print(x)
```

Output (exemplu):

```
14
```

## Exemplu 4 — Doar Numere Impare între 1 și 99

```python
import random

x = random.randrange(1, 100, 2)
print(x)
```

Output (exemplu):

```
57
```

## Exemplu 5 — Multipli de 5 între 0 și 100

```python
import random

x = random.randrange(0, 105, 5)
print(x)
```

Output (exemplu):

```
75
```

## Exemplu 6 — Index Aleator pentru o Listă

```python
import random

fructe = ["mar", "para", "banana", "kiwi"]

index = random.randrange(len(fructe))
print(fructe[index])
```

Output (exemplu):

```
kiwi
```

Explicație:

`random.randrange(len(fructe))` generează un index valid pentru listă (`0` până la `len(fructe) - 1`), la fel cum ar face `random.randint(0, len(fructe) - 1)`.

## Exemplu 7 — Pas Negativ (la Fel ca la `range()`)

```python
import random

x = random.randrange(20, 0, -2)
print(x)
```

Output (exemplu):

```
14
```

Explicație:

Cu pas negativ, `start` trebuie să fie mai mare decât `stop`. Rezultatul este ales din `20, 18, 16, ..., 2`.

## Exemplu 8 — Generarea a 5 Numere din 3 în 3

```python
import random

for i in range(5):
    print(random.randrange(0, 30, 3))
```

Output (exemplu):

```
9
0
21
18
27
```

---

# 5. `randint()` vs. `randrange()` — Diferența

| Funcție | Capătul final | Pas |
|---|---|---|
| `random.randint(a, b)` | **inclus** | nu |
| `random.randrange(a, b)` | **exclus** (ca la `range()`) | da, opțional |

```python
import random

print(random.randint(1, 5))      # poate genera și 5
print(random.randrange(1, 5))    # nu poate genera 5, doar 1-4
```

---

# 6. Exemplu Complet — Joc "Ghicește Numărul"

```python
import random

numar_secret = random.randint(1, 20)
incercare = int(input("Ghicește un număr între 1 și 20: "))

if incercare == numar_secret:
    print("Ai ghicit!")
elif incercare < numar_secret:
    print("Prea mic!")
else:
    print("Prea mare!")
```

Exemplu de interacțiune:

```
Ghicește un număr între 1 și 20: 15
Prea mic!
```

---

# 7. Rezumat

* `import random` — obligatoriu înainte de a folosi modulul
* `random.random()` — float aleator, `0.0 <= x < 1.0`, util pentru probabilități și valori zecimale
* `random.randint(a, b)` — întreg aleator, **capete incluse**
* `random.randrange(start, stop, pas)` — ca `range()`, **`stop` exclus**, pas opțional
* `randint(a, b)` include `b`; `randrange(a, b)` **nu** include `b`
* toate pot fi combinate cu bucle `for` sau list comprehension pentru a genera mai multe valori deodată
