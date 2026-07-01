# List Comprehension în Python — Definiție și Exemple

Acest document explică **list comprehension**: o modalitate compactă de a crea liste noi, pornind de la alte liste sau iterabile.

---

# 1. Ce Este List Comprehension?

**List comprehension** este o sintaxă scurtă care permite crearea unei liste noi într-o singură linie, în loc de a folosi o buclă `for` clasică cu `append()`.

Sintaxă generală:

```python
lista_noua = [expresie for element in iterabil]
```

* `expresie` — ce se calculează/pune în lista nouă pentru fiecare element
* `element` — variabila curentă din iterabil
* `iterabil` — lista/range/string peste care se parcurge

---

# 2. Comparație: For Clasic vs. List Comprehension

## Cu buclă `for` clasică

```python
patrate = []
for x in range(1, 6):
    patrate.append(x ** 2)

print(patrate)
```

## Cu list comprehension

```python
patrate = [x ** 2 for x in range(1, 6)]
print(patrate)
```

Output (identic pentru ambele variante):

```
[1, 4, 9, 16, 25]
```

Explicație:

List comprehension face exact același lucru ca bucla `for` + `append()`, dar mai scurt și mai citit ca o singură expresie.

---

# 3. Exemple Simple

## Exemplu 1 — Dublarea Numerelor

```python
numere = [1, 2, 3, 4]
dublate = [n * 2 for n in numere]
print(dublate)
```

Output:

```
[2, 4, 6, 8]
```

## Exemplu 2 — Lungimea Fiecărui Cuvânt

```python
cuvinte = ["ana", "bogdan", "carmen"]
lungimi = [len(c) for c in cuvinte]
print(lungimi)
```

Output:

```
[3, 6, 7]
```

## Exemplu 3 — Litere Mari

```python
nume = ["ana", "ion", "maria"]
nume_mari = [n.upper() for n in nume]
print(nume_mari)
```

Output:

```
['ANA', 'ION', 'MARIA']
```

---

# 4. List Comprehension cu Condiție (`if`)

Sintaxă:

```python
lista_noua = [expresie for element in iterabil if conditie]
```

Doar elementele pentru care condiția este `True` ajung în lista nouă.

## Exemplu 1 — Doar Numerele Pare

```python
numere = [1, 2, 3, 4, 5, 6]
pare = [n for n in numere if n % 2 == 0]
print(pare)
```

Output:

```
[2, 4, 6]
```

## Exemplu 2 — Doar Cuvintele Mai Lungi de 3 Litere

```python
cuvinte = ["ana", "bogdan", "ion", "carmen"]
lungi = [c for c in cuvinte if len(c) > 3]
print(lungi)
```

Output:

```
['bogdan', 'carmen']
```

---

# 5. List Comprehension cu `if...else`

Sintaxă (atenție, ordinea diferă față de `if` simplu):

```python
lista_noua = [expresie_daca_adevarat if conditie else expresie_daca_fals for element in iterabil]
```

## Exemplu — Par sau Impar

```python
numere = [1, 2, 3, 4, 5]
etichete = ["par" if n % 2 == 0 else "impar" for n in numere]
print(etichete)
```

Output:

```
['impar', 'par', 'impar', 'par', 'impar']
```

Explicație:

Aici `if...else` face parte din **expresie** (ce se pune în listă), nu filtrează elementele — de aceea lista rezultată are aceeași lungime ca lista originală.

---

# 6. List Comprehension pe un `range`

```python
cuburi = [x ** 3 for x in range(1, 6)]
print(cuburi)
```

Output:

```
[1, 8, 27, 64, 125]
```

---

# 7. List Comprehension pe un String

Un string este un iterabil de caractere, deci poate fi folosit direct.

```python
text = "python"
litere_mari = [litera.upper() for litera in text]
print(litere_mari)
```

Output:

```
['P', 'Y', 'T', 'H', 'O', 'N']
```

---

# 8. List Comprehension Imbricat (Nested)

Se pot folosi două (sau mai multe) bucle `for` în aceeași list comprehension, la fel ca niște bucle imbricate.

```python
perechi = [(x, y) for x in range(1, 3) for y in range(1, 3)]
print(perechi)
```

Output:

```
[(1, 1), (1, 2), (2, 1), (2, 2)]
```

Explicație:

Este echivalent cu:

```python
perechi = []
for x in range(1, 3):
    for y in range(1, 3):
        perechi.append((x, y))
```

Acest tip de list comprehension imbricat este folosit și pentru **matrici** — vezi documentul dedicat.

---

# 9. Rezumat

* Sintaxă de bază: `[expresie for element in iterabil]`
* Cu filtrare: `[expresie for element in iterabil if conditie]`
* Cu alegere condiționată (parte din expresie): `[a if conditie else b for element in iterabil]`
* Poate fi folosit pe liste, `range()`, string-uri sau orice iterabil
* Poate avea mai multe bucle `for` imbricate, într-o singură linie
* Face exact ce ar face o buclă `for` + `append()`, dar mai concis
