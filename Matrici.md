# Matrici în Python — Definiție și List Comprehension

Acest document explică cum se reprezintă **matricile** în Python folosind liste imbricate, și cum se pot crea/parcurge eficient cu **list comprehension**.

Se recomandă citirea documentelor [Liste.md](Liste.md) și [List-comprehension.md](List-comprehension.md) înainte de acesta.

---

# 1. Ce Este o Matrice în Python?

Python nu are un tip de date `matrice` separat — o matrice este reprezentată ca o **listă de liste**, unde fiecare listă interioară este un **rând**.

```python
matrice = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Aceasta este o matrice cu **3 rânduri** și **3 coloane** (3x3).

---

# 2. Accesarea Elementelor

Sintaxă: `matrice[rand][coloana]` — indecșii încep de la `0`.

```python
matrice = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matrice[0])        # primul rând -> [1, 2, 3]
print(matrice[1][2])     # rândul 1, coloana 2 -> 6
print(matrice[-1])       # ultimul rând -> [7, 8, 9]
```

Output:

```
[1, 2, 3]
6
[7, 8, 9]
```

---

# 3. Parcurgerea unei Matrice cu Bucle `for` Clasice

```python
matrice = [
    [1, 2, 3],
    [4, 5, 6]
]

for rand in matrice:
    for element in rand:
        print(element, end=" ")
    print()
```

Output:

```
1 2 3
4 5 6
```

Explicație:

Bucla exterioară parcurge fiecare **rând**; bucla interioară parcurge fiecare **element** din rândul curent.

---

# 4. Crearea unei Matrice cu List Comprehension

## Exemplu 1 — Matrice cu Toate Elementele 0

```python
linii = 3
coloane = 4

matrice = [[0 for c in range(coloane)] for r in range(linii)]
print(matrice)
```

Output:

```
[[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
```

Explicație:

* Comprehension-ul **interior** `[0 for c in range(coloane)]` creează **un rând** cu `coloane` zerouri.
* Comprehension-ul **exterior** `[... for r in range(linii)]` repetă acest rând de `linii` ori.

## Exemplu 2 — Tabla Înmulțirii (Matrice 5x5)

```python
n = 5
tabla = [[r * c for c in range(1, n + 1)] for r in range(1, n + 1)]

for rand in tabla:
    print(rand)
```

Output:

```
[1, 2, 3, 4, 5]
[2, 4, 6, 8, 10]
[3, 6, 9, 12, 15]
[4, 8, 12, 16, 20]
[5, 10, 15, 20, 25]
```

---

# 5. List Comprehension cu Condiție generare matrice

Matricea identitate are `1` pe diagonala principală și `0` în rest.

```python
n = 4
identitate = [[1 if r == c else 0 for c in range(n)] for r in range(n)]

for rand in identitate:
    print(rand)
```

Output:

```
[1, 0, 0, 0]
[0, 1, 0, 0]
[0, 0, 1, 0]
[0, 0, 0, 1]
```

Explicație:

Pentru fiecare poziție `(r, c)`, punem `1` dacă suntem pe diagonală (`r == c`), altfel punem `0`.


---

# 7. Suma Elementelor unei Matrice

## Cu bucle `for` clasice

```python
matrice = [
    [1, 2, 3],
    [4, 5, 6]
]

suma = 0
for rand in matrice:
    for element in rand:
        suma += element

print(suma)
```



---

# 8. Rezumat

* O matrice este o **listă de liste**; fiecare listă interioară este un rând.
* Accesare: `matrice[rand][coloana]`.
* Parcurgere: două bucle `for` imbricate (una pentru rânduri, una pentru elemente).
* Creare cu list comprehension: `[[expresie for c in range(coloane)] for r in range(linii)]`.

