# Funcția `range()` în Python — Definiție și Exemple

Acest document explică funcția **built-in** `range()`, folosită mai ales pentru a repeta o bucată de cod de un anumit număr de ori.

---

# 1. Ce Este `range()`?

`range()` generează o secvență de numere întregi, folosită de obicei într-o buclă `for`.

* nu creează o listă în memorie, ci un obiect special de tip `range`, care generează valorile pe rând (eficient pentru secvențe mari)
* capătul final (`stop`) este întotdeauna **exclus**

Forme posibile:

```python
range(stop)               # de la 0 la stop (exclus)
range(start, stop)        # de la start la stop (exclus)
range(start, stop, pas)   # de la start la stop (exclus), cu un pas dat
```

---

# 2. `range(stop)` — Un Singur Argument

Începe implicit de la `0`.

## Exemplu 1

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

`range(5)` generează `0, 1, 2, 3, 4` — nu include `5`.

## Exemplu 2 — Repetarea unei Acțiuni de N Ori

```python
for i in range(3):
    print("Salut!")
```

Output:

```
Salut!
Salut!
Salut!
```

---

# 3. `range(start, stop)` — Două Argumente

## Exemplu 1

```python
for i in range(2, 7):
    print(i)
```

Output:

```
2
3
4
5
6
```

## Exemplu 2 — Numărătoare de la 1

```python
for i in range(1, 6):
    print(i)
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

`range(1, 6)` generează `1, 2, 3, 4, 5` — folosit des când vrem numerotare naturală (1, 2, 3...) în loc de a începe de la 0.

---

# 4. `range(start, stop, pas)` — Trei Argumente

## Exemplu 1 — Numere Pare

```python
for i in range(0, 10, 2):
    print(i)
```

Output:

```
0
2
4
6
8
```

## Exemplu 2 — Numere Impare

```python
for i in range(1, 10, 2):
    print(i)
```

Output:

```
1
3
5
7
9
```

## Exemplu 3 — Pas Negativ (Numărătoare Inversă)

```python
for i in range(10, 0, -1):
    print(i)
```

Output:

```
10
9
8
7
6
5
4
3
2
1
```

Explicație:

Dacă `pas` este negativ, `start` trebuie să fie **mai mare** decât `stop`, altfel `range()` nu generează niciun număr.

## Exemplu 4 — Sărituri Mai Mari

```python
for i in range(0, 30, 5):
    print(i)
```

Output:

```
0
5
10
15
20
25
```

---

# 5. `range()` Gol (Nicio Valoare Generată)

```python
for i in range(5, 5):
    print(i)

print("Gata.")
```

Output:

```
Gata.
```

Explicație:

Dacă `start == stop` (sau `start` "trece" de `stop` fără pasul potrivit), `range()` nu generează nimic, iar bucla `for` nu se execută deloc.

---

# 6. `range()` Folosit cu `len()` — Parcurgere după Index

```python
fructe = ["mar", "para", "banana"]

for i in range(len(fructe)):
    print(i, "-", fructe[i])
```

Output:

```
0 - mar
1 - para
2 - banana
```

Explicație:

`range(len(fructe))` generează indecșii `0, 1, 2`, utili când avem nevoie și de poziția elementului, nu doar de valoare (deși pentru acest caz `enumerate()` este de obicei preferat).


---

# 8. `range()` în List Comprehension

```python
patrate = [x ** 2 for x in range(1, 6)]
print(patrate)
```

Output:

```
[1, 4, 9, 16, 25]
```

Explicație:

`range()` este folosit foarte des ca sursă de valori pentru list comprehension (vezi documentul [List-comprehension.md](List-comprehension.md)).

---

# 9. Exemplu Complet — Tabla Înmulțirii cu 7

```python
numar = 7

for i in range(1, 11):
    print(numar, "x", i, "=", numar * i)
```

Output:

```
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
```

---

# 10. Rezumat

* `range(stop)` — de la `0` la `stop` (exclus)
* `range(start, stop)` — de la `start` la `stop` (exclus)
* `range(start, stop, pas)` — cu pas personalizat; pasul poate fi și negativ (numărătoare inversă)
* capătul `stop` este **întotdeauna exclus**
* `range()` nu este o listă — pentru a obține o listă, se folosește `list(range(...))`
* folosit frecvent în bucle `for`, cu `len()` pentru parcurgere după index, sau ca sursă pentru list comprehension
