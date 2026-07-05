# `if`, `for`, `while` — Condiții și Bucle în Python

Acest document explică **structurile de control** din Python: condiția `if`/`elif`/`else`, bucla `while`, bucla `for` (inclusiv parcurgerea directă a elementelor unei colecții), și modul în care `break`, `continue` și clauza `else` funcționează pe bucle.

---

# 1. Condiția `if`

## 1.1. Sintaxă de Bază

```python
varsta = 20

if varsta >= 18:
    print("Ești major.")
```

Output:

```
Ești major.
```

Explicație:

Blocul indentat de sub `if` se execută **doar dacă** expresia de după `if` este `True`.

## 1.2. `if` / `else`

```python
varsta = 15

if varsta >= 18:
    print("Ești major.")
else:
    print("Ești minor.")
```

Output:

```
Ești minor.
```

## 1.3. `if` / `elif` / `else`

```python
nota = 7

if nota >= 9:
    print("Excelent")
elif nota >= 7:
    print("Bine")
elif nota >= 5:
    print("Suficient")
else:
    print("Insuficient")
```

Output:

```
Bine
```

Explicație:

Python verifică condițiile **în ordine**, de sus în jos, și execută **doar primul** bloc a cărui condiție este `True`; restul sunt ignorate, chiar dacă ar fi și ele adevărate.

## 1.4. Condiții Imbricate (Nested `if`)

```python
varsta = 20
are_permis = True

if varsta >= 18:
    if are_permis:
        print("Poate conduce.")
    else:
        print("Are vârsta, dar nu are permis.")
else:
    print("Este minor.")
```

Output:

```
Poate conduce.
```

---

# 2. Bucla `while`

`while` repetă un bloc de cod **atât timp cât** o condiție rămâne `True`.

## 2.1. Sintaxă de Bază

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

Output:

```
1
2
3
4
5
```

Explicație:

Condiția este verificată **înainte** de fiecare repetare. Dacă `i` nu ar fi incrementat, bucla ar rula la infinit.

## 2.2. `while True` cu Ieșire Condiționată

```python
numar = 0

while True:
    numar += 1
    if numar == 3:
        break
    print(numar)
```

Output:

```
1
2
```

Explicație:

`while True` creează o buclă infinită prin construcție; singura cale de ieșire este un `break` executat undeva în interior (vezi secțiunea 5).

---

# 3. Bucla `for`

`for` parcurge elementele unei secvențe (listă, string, `range`, etc.), rând pe rând.

## 3.1. `for` cu `range()`

```python
for i in range(5):
    print(i)
```

Output:

```
0
1
2
3
4
```

Explicație:

`range(5)` generează numerele `0, 1, 2, 3, 4` (vezi [Range.md](Range.md)); `stop` (`5`) este **exclus**.

## 3.2. `for` cu `range(start, stop, pas)`

```python
for i in range(2, 10, 2):
    print(i)
```

Output:

```
2
4
6
8
```

---

# 4. Parcurgerea Directă a unei Colecții cu `for`

`for` poate parcurge **direct elementele** unei colecții (listă, tuplu, string, dicționar), fără a folosi un index.

## 4.1. Parcurgerea unei Liste

```python
fructe = ["mar", "para", "banana"]

for fruct in fructe:
    print(fruct)
```

Output:

```
mar
para
banana
```

## 4.2. Parcurgerea unui String

```python
for litera in "abc":
    print(litera)
```

Output:

```
a
b
c
```

## 4.3. Parcurgerea unui Dicționar

```python
student = {"nume": "Alice", "varsta": 20}

for cheie, valoare in student.items():
    print(cheie, ":", valoare)
```

Output:

```
nume : Alice
varsta : 20
```

Explicație:

Vezi [Dictionare.md](Dictionare.md) pentru mai multe detalii despre `.items()`, `.keys()` și `.values()`.

---

# 5. `break` — Oprirea Completă a Buclei

`break` **oprește imediat** bucla curentă (`for` sau `while`), indiferent dacă mai erau elemente/condiții de parcurs.

## 5.1. `break` într-un `for`

```python
numere = [1, 2, 3, 4, 5]

for numar in numere:
    if numar == 3:
        break
    print(numar)
```

Output:

```
1
2
```

Explicație:

Când `numar` devine `3`, bucla se oprește complet — `4` și `5` nu mai sunt afișate.

## 5.2. `break` într-un `while`

```python
i = 0

while i < 10:
    if i == 4:
        break
    print(i)
    i += 1
```

Output:

```
0
1
2
3
```

---

# 6. `continue` — Sărirea Peste Iterația Curentă

`continue` **oprește doar iterația curentă** și trece direct la următoarea, fără să oprească toată bucla.

## 6.1. `continue` într-un `for`

```python
for numar in range(1, 6):
    if numar == 3:
        continue
    print(numar)
```

Output:

```
1
2
4
5
```

Explicație:

Când `numar` este `3`, `print(numar)` este sărit pentru acea iterație, dar bucla continuă normal cu `4` și `5`.

## 6.2. `continue` într-un `while`

```python
i = 0

while i < 5:
    i += 1
    if i % 2 == 0:
        continue
    print(i)
```

Output:

```
1
3
5
```

Explicație:

Numerele pare sunt sărite prin `continue`; sunt afișate doar cele impare.

---

# 7. Clauza `else` pe Bucle (`for...else`, `while...else`)

O buclă `for` sau `while` poate avea și un bloc `else`, care se execută **doar dacă bucla s-a terminat normal**, adică **fără** să fi fost întreruptă cu `break`.

## 7.1. `for...else` — Fără `break`

```python
for i in range(3):
    print(i)
else:
    print("Bucla s-a terminat normal.")
```

Output:

```
0
1
2
Bucla s-a terminat normal.
```

## 7.2. `for...else` — Cu `break`

```python
numere = [1, 2, 3, 4, 5]

for numar in numere:
    if numar == 3:
        print("Am găsit 3!")
        break
else:
    print("Nu am găsit 3.")
```

Output:

```
Am găsit 3!
```

Explicație:

Deoarece bucla a fost oprită cu `break`, blocul `else` **nu se mai execută**. Acest tipar este folosit des la căutări: `else` rulează doar dacă elementul căutat **nu** a fost găsit.

## 7.3. `for...else` — Căutare Fără Rezultat

```python
numere = [1, 2, 4, 5]

for numar in numere:
    if numar == 3:
        print("Am găsit 3!")
        break
else:
    print("Nu am găsit 3.")
```

Output:

```
Nu am găsit 3.
```

## 7.4. `while...else`

```python
i = 0

while i < 3:
    print(i)
    i += 1
else:
    print("Condiția a devenit falsă, bucla s-a terminat normal.")
```

Output:

```
0
1
2
Condiția a devenit falsă, bucla s-a terminat normal.
```

---

# 8. Rezumat

* `if` / `elif` / `else` — execută un bloc de cod în funcție de o condiție; doar primul bloc adevărat este rulat
* `while` — repetă un bloc **atât timp cât** o condiție rămâne `True`; verifică condiția **înainte** de fiecare repetare
* `for` — parcurge o secvență (des folosit cu `range()`)
* `for element in colectie` — parcurge direct elementele unei liste, string sau dicționar (`.items()`), fără index explicit
* `break` — oprește **complet** bucla curentă
* `continue` — sare peste **restul iterației curente**, dar bucla continuă
* `else` pe `for`/`while` — se execută **doar dacă** bucla s-a terminat normal, **fără** `break`; util pentru tipare de căutare ("nu am găsit nimic")
