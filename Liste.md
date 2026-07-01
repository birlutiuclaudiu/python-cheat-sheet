# Liste în Python — Definiție, Metode și Exemple

Acest document explică **listele** în Python: ce sunt, cum se creează, cum se accesează și modifică elementele, și cele mai folosite metode.

---

# 1. Ce Este o Listă?

O **listă** este o colecție **ordonată** și **mutabilă** de elemente.

* ordonată → elementele au o poziție fixă (index), în ordinea în care au fost adăugate
* mutabilă → poate fi modificată după ce a fost creată (adăugare, ștergere, schimbare valori)
* poate conține elemente de **tipuri diferite** (numere, text, alte liste etc.)

```python
numere = [1, 2, 3, 4]
nume = ["Ana", "Bogdan", "Carmen"]
mixt = [10, "text", True, 3.5]
lista_goala = []
```

---

# 2. Accesarea Elementelor

Elementele au un index care începe de la **0**. Se pot folosi și indecși **negativi**, care numără de la finalul listei.

```python
numere = [10, 20, 30, 40, 50]

print(numere[0])     # 10 (primul element)
print(numere[2])     # 30
print(numere[-1])    # 50 (ultimul element)
print(numere[-2])    # 40 (penultimul element)
```

Output:

```
10
30
50
40
```

---

# 3. Slicing (Extragerea unei Porțiuni din Listă)

Sintaxă: `lista[start:stop:pas]` — `stop` este **exclus**.

```python
numere = [10, 20, 30, 40, 50]

print(numere[1:3])     # de la poziția 1 la 3 (exclus)
print(numere[:2])      # de la început până la poziția 2 (exclus)
print(numere[2:])      # de la poziția 2 până la final
print(numere[::-1])    # întreaga listă, inversată
```

Output:

```
[20, 30]
[10, 20]
[30, 40, 50]
[50, 40, 30, 20, 10]
```

---

# 4. Modificarea Elementelor

```python
numere = [10, 20, 30]
numere[1] = 99
print(numere)
```

Output:

```
[10, 99, 30]
```

Explicație:

Spre deosebire de un `tuple`, o listă este **mutabilă**, deci elementele ei pot fi schimbate direct prin index.

---

# 5. Metode Utile pentru Liste

## `append()` — Adaugă un Element la Final

```python
fructe = ["mar", "para"]
fructe.append("banana")
print(fructe)
```

Output:

```
['mar', 'para', 'banana']
```

## `insert()` — Adaugă un Element la o Poziție Specifică

```python
fructe = ["mar", "para"]
fructe.insert(1, "kiwi")
print(fructe)
```

Output:

```
['mar', 'kiwi', 'para']
```

## `remove()` — Șterge Prima Apariție a unei Valori

```python
fructe = ["mar", "para", "mar"]
fructe.remove("mar")
print(fructe)
```

Output:

```
['para', 'mar']
```

## `pop()` — Scoate și Returnează un Element (Implicit, Ultimul)

```python
fructe = ["mar", "para", "banana"]
ultimul = fructe.pop()
print(ultimul)
print(fructe)
```

Output:

```
banana
['mar', 'para']
```

## `sort()` — Sortează Lista (Modifică Lista Originală)

```python
numere = [5, 2, 8, 1]
numere.sort()
print(numere)

numere.sort(reverse=True)
print(numere)
```

Output:

```
[1, 2, 5, 8]
[8, 5, 2, 1]
```

## `reverse()` — Inversează Ordinea Elementelor

```python
numere = [1, 2, 3]
numere.reverse()
print(numere)
```

Output:

```
[3, 2, 1]
```

## `extend()` — Adaugă Toate Elementele Dintr-o Altă Listă

```python
a = [1, 2]
b = [3, 4]
a.extend(b)
print(a)
```

Output:

```
[1, 2, 3, 4]
```

## `len()`, `index()`, `count()`

```python
numere = [10, 20, 30, 20]

print(len(numere))         # numărul de elemente
print(numere.index(30))    # poziția primei apariții a valorii 30
print(numere.count(20))    # de câte ori apare valoarea 20
```

Output:

```
4
2
2
```

## `clear()` — Golește Lista

```python
numere = [1, 2, 3]
numere.clear()
print(numere)
```

Output:

```
[]
```

---

# 6. Parcurgerea unei Liste

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

## Parcurgere cu Index — `enumerate()`

```python
fructe = ["mar", "para", "banana"]

for index, fruct in enumerate(fructe):
    print(index, "-", fruct)
```

Output:

```
0 - mar
1 - para
2 - banana
```

---

# 7. Liste Imbricate (Liste de Liste)

O listă poate conține alte liste ca elemente. Acest lucru este folosit pentru a reprezenta **matrici** (vezi documentul dedicat matricilor).

```python
matrice = [
    [1, 2, 3],
    [4, 5, 6]
]

print(matrice[0])       # [1, 2, 3] - primul rând
print(matrice[0][1])    # 2 - elementul de pe rândul 0, coloana 1
```

Output:

```
[1, 2, 3]
2
```

---

# 8. Copierea Listelor — Referință vs. Copie Reală

```python
a = [1, 2, 3]
b = a               # b este aceeași listă ca a (referință)
b.append(4)
print(a)             # a s-a modificat și ea!

c = [1, 2, 3]
d = c.copy()        # d este o copie reală, independentă
d.append(4)
print(c)             # c rămâne neschimbat
print(d)
```

Output:

```
[1, 2, 3, 4]
[1, 2, 3]
[1, 2, 3, 4]
```

Explicație:

`b = a` nu creează o listă nouă, ci doar o altă etichetă pentru **aceeași** listă. Pentru o copie independentă, se folosește `.copy()` sau `list(a)`.

---

# 9. Rezumat

* O **listă** este ordonată, mutabilă, poate conține tipuri diferite: `[1, "a", True]`
* Indexare: `lista[0]` (primul), `lista[-1]` (ultimul)
* Slicing: `lista[start:stop:pas]`, capătul `stop` e exclus
* Metode principale: `append`, `insert`, `remove`, `pop`, `sort`, `reverse`, `extend`, `clear`
* `len()`, `index()`, `count()` oferă informații despre listă
* Parcurgere cu `for element in lista` sau `for i, element in enumerate(lista)`
* O listă poate conține alte liste (liste imbricate → matrici)
* `b = a` copiază **referința**, nu lista; pentru o copie reală se folosește `.copy()`
