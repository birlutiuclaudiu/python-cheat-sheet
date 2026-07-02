# Dicționare în Python — Definiție, Metode și Exemple

Acest document explică **dicționarele** (`dict`) în Python: ce sunt, cum se creează, cum se accesează și modifică valorile, și cele mai folosite metode.

---

# 1. Ce Este un Dicționar?

Un **dicționar** este o colecție **mutabilă** care stochează date sub formă de perechi **cheie-valoare**.

* fiecare **cheie** este unică și se folosește pentru a găsi rapid o **valoare**
* cheile sunt de obicei string-uri sau numere; valorile pot fi de orice tip
* de la Python 3.7, dicționarele **păstrează ordinea** în care au fost adăugate elementele

```python
student = {
    "nume": "Alice",
    "varsta": 20,
    "nota": 9.5
}
```

---

# 2. Accesarea Valorilor

## Cu `[]`

```python
student = {"nume": "Alice", "varsta": 20}
print(student["nume"])
```

Output:

```
Alice
```

Dacă cheia nu există, `[]` produce o eroare (`KeyError`).

## Cu `.get()` — Variantă Sigură

```python
student = {"nume": "Alice", "varsta": 20}

print(student.get("varsta"))          # 20
print(student.get("oras"))            # None (cheia nu există)
print(student.get("oras", "necunoscut"))   # valoare implicită dacă cheia lipsește
```

Output:

```
20
None
necunoscut
```

Explicație:

`.get()` nu produce eroare dacă cheia nu există — returnează `None` sau valoarea implicită dată ca al doilea argument.

---

# 3. Adăugarea și Modificarea Valorilor

```python
student = {"nume": "Alice", "varsta": 20}

student["varsta"] = 21           # modifică o valoare existentă
student["oras"] = "Cluj"         # adaugă o cheie nouă

print(student)
```

Output:

```
{'nume': 'Alice', 'varsta': 21, 'oras': 'Cluj'}
```

Explicație:

Dacă cheia există deja, valoarea se **suprascrie**; dacă nu există, se **adaugă** o pereche cheie-valoare nouă.

---

# 4. Ștergerea Elementelor

## `del` — Șterge o Cheie

```python
student = {"nume": "Alice", "varsta": 20, "oras": "Cluj"}
del student["oras"]
print(student)
```

Output:

```
{'nume': 'Alice', 'varsta': 20}
```

## `.pop()` — Șterge și Returnează Valoarea

```python
student = {"nume": "Alice", "varsta": 20}
varsta = student.pop("varsta")

print(varsta)
print(student)
```

Output:

```
20
{'nume': 'Alice'}
```

---

# 5. Verificarea Existenței unei Chei

```python
student = {"nume": "Alice", "varsta": 20}

print("nume" in student)
print("oras" in student)
```

Output:

```
True
False
```

Explicație:

Operatorul `in` verifică dacă o **cheie** există în dicționar (nu o valoare).

---

# 6. Parcurgerea unui Dicționar

## Parcurgerea Cheilor — `.keys()`

```python
student = {"nume": "Alice", "varsta": 20, "oras": "Cluj"}

for cheie in student.keys():
    print(cheie)
```

Output:

```
nume
varsta
oras
```

## Parcurgerea Valorilor — `.values()`

```python
for valoare in student.values():
    print(valoare)
```

Output:

```
Alice
20
Cluj
```

## Parcurgerea Perechilor Cheie-Valoare — `.items()`

```python
for cheie, valoare in student.items():
    print(cheie, ":", valoare)
```

Output:

```
nume : Alice
varsta : 20
oras : Cluj
```

Explicație:

`.items()` este cea mai folosită metodă de parcurgere, pentru că oferă acces direct atât la cheie, cât și la valoare.

---

# 7. Alte Metode Utile

## `len()` — Numărul de Perechi Cheie-Valoare

```python
student = {"nume": "Alice", "varsta": 20}
print(len(student))
```

Output:

```
2
```

## `.update()` — Combină Două Dicționare

```python
student = {"nume": "Alice", "varsta": 20}
student.update({"varsta": 21, "oras": "Cluj"})
print(student)
```

Output:

```
{'nume': 'Alice', 'varsta': 21, 'oras': 'Cluj'}
```

Explicație:

`.update()` adaugă cheile noi și **suprascrie** valorile pentru cheile care există deja.

## `.copy()` — Copie Reală, Independentă

```python
a = {"x": 1}
b = a.copy()
b["x"] = 99

print(a)
print(b)
```

Output:

```
{'x': 1}
{'x': 99}
```

## `.clear()` — Golește Dicționarul

```python
student = {"nume": "Alice", "varsta": 20}
student.clear()
print(student)
```

Output:

```
{}
```

---

# 8. Dicționar Imbricat (Dicționar de Dicționare)

Un dicționar poate avea drept valori alte dicționare — util pentru a reprezenta mai multe înregistrări.

```python
studenti = {
    "s1": {"nume": "Alice", "nota": 9.5},
    "s2": {"nume": "Bogdan", "nota": 8.0}
}

print(studenti["s1"]["nume"])   # Alice
print(studenti["s2"]["nota"])   # 8.0

for cod, info in studenti.items():
    print(cod, "->", info["nume"], info["nota"])
```

Output:

```
Alice
8.0
s1 -> Alice 9.5
s2 -> Bogdan 8.0
```

---

# 10. Rezumat

* Un **dicționar** stochează perechi **cheie-valoare**: `{"cheie": "valoare"}`
* Accesare: `dict["cheie"]` (produce eroare dacă lipsește) sau `dict.get("cheie", implicit)` (variantă sigură)
* Adăugare/modificare: `dict["cheie"] = valoare`
* Ștergere: `del dict["cheie"]` sau `dict.pop("cheie")`
* Verificare existență: `"cheie" in dict`
* Parcurgere: `.keys()`, `.values()`, `.items()` (cea mai folosită)
* Alte metode: `.update()`, `.copy()`, `.clear()`, `len()`
* Un dicționar poate conține alte dicționare (structuri imbricate)
* **Dictionary comprehension**: `{cheie: valoare for element in iterabil}`
