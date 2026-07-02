# Excepții în Python — `try`/`except` și Cele Mai Cunoscute Erori

Acest document explică **excepțiile** în Python: ce sunt, cum se tratează cu `try`/`except`, și oferă exemple pentru cele mai întâlnite tipuri de erori — `TypeError`, `ValueError`, `ZeroDivisionError` și altele.

---

# 1. Ce Este o Excepție?

O **excepție** este o eroare care apare **în timpul rulării** programului și care, dacă nu este tratată, oprește execuția programului.

```python
numar = int("abc")
```

Output:

```
Traceback (most recent call last):
ValueError: invalid literal for int() with base 10: 'abc'
```

Explicație:

Codul de mai sus este corect scris (nu are eroare de sintaxă), dar produce o eroare **la rulare**, pentru că `"abc"` nu poate fi transformat într-un număr întreg.

---

# 2. `try` / `except` — Sintaxă de Bază

```python
try:
    # cod care poate produce o eroare
    ...
except NumeExceptie:
    # cod care se execută dacă apare acea eroare
    ...
```

```python
try:
    numar = int("abc")
except ValueError:
    print("Nu este un număr valid!")
```

Output:

```
Nu este un număr valid!
```

Explicație:

Codul din blocul `try` este executat normal. Dacă apare o eroare de tipul specificat în `except`, programul **nu se oprește** — execută în schimb codul din `except`.

---

# 3. `TypeError` — Operație pe un Tip de Date Greșit

`TypeError` apare când o operație sau funcție este folosită cu un tip de date incompatibil.

## Exemplu 1 — Adunarea unui Număr cu un Text

```python
rezultat = 5 + "3"
```

Output:

```
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

## Exemplu 2 — Tratarea Erorii

```python
try:
    rezultat = 5 + "3"
except TypeError:
    print("Nu poți aduna un număr cu un text!")
```

Output:

```
Nu poți aduna un număr cu un text!
```

## Exemplu 3 — Apelarea unui Element care Nu Este Funcție

```python
numar = 5
numar()
```

Output:

```
TypeError: 'int' object is not callable
```

Explicație:

Eroarea apare pentru că `numar` este un întreg, nu o funcție — `()` încearcă să îl "apeleze" ca și cum ar fi una.

## Exemplu 4 — `len()` pe un Tip care Nu Are Lungime

```python
x = 5
print(len(x))
```

Output:

```
TypeError: object of type 'int' has no len()
```

## Exemplu 5 — Concatenarea unei Liste cu un Element care Nu E Listă

```python
numere = [1, 2, 3]
rezultat = numere + 4
```

Output:

```
TypeError: can only concatenate list (not "int") to list
```

## Exemplu 6 — Prea Multe/Puține Argumente la o Funcție

```python
def aduna(a, b):
    return a + b

print(aduna(5))
```

Output:

```
TypeError: aduna() missing 1 required positional argument: 'b'
```

## Exemplu 7 — Tratarea în Context (Funcție Sigură de Adunare)

```python
def aduna_sigur(a, b):
    try:
        return a + b
    except TypeError:
        return "Ambele valori trebuie să fie de același tip compatibil!"

print(aduna_sigur(5, 3))
print(aduna_sigur(5, "3"))
```

Output:

```
8
Ambele valori trebuie să fie de același tip compatibil!
```

---

# 4. `ValueError` — Valoare de Tip Corect, dar Invalidă

`ValueError` apare când o funcție primește un argument de **tipul corect**, dar cu o **valoare** pe care nu o poate procesa.

## Exemplu 1 — Conversie Text Invalid în `int`

```python
numar = int("abc")
```

Output:

```
ValueError: invalid literal for int() with base 10: 'abc'
```

## Exemplu 2 — Tratarea Erorii la Citirea de la Utilizator

```python
try:
    varsta = int(input("Introdu vârsta: "))
    print("Vârsta ta este", varsta)
except ValueError:
    print("Trebuie să introduci un număr întreg!")
```

Exemplu de interacțiune:

```
Introdu vârsta: douazeci
Trebuie să introduci un număr întreg!
```

## Exemplu 3 — Conversie Text Invalid în `float`

```python
pret = float("12,5")   # virgulă în loc de punct
```

Output:

```
ValueError: could not convert string to float: '12,5'
```

## Exemplu 4 — `list.remove()` cu o Valoare Inexistentă

```python
numere = [1, 2, 3]
numere.remove(10)
```

Output:

```
ValueError: list.remove(x): x not in list
```

## Exemplu 5 — Despachetare (Unpacking) cu Număr Greșit de Valori

```python
a, b = [1, 2, 3]
```

Output:

```
ValueError: too many values to unpack (expected 2)
```

## Exemplu 6 — `.index()` cu o Valoare care Nu Există

```python
fructe = ["mar", "para"]
pozitie = fructe.index("banana")
```

Output:

```
ValueError: 'banana' is not in list
```

## Exemplu 7 — Validarea Vârstei cu `ValueError` Ridicat Manual

```python
def seteaza_varsta(varsta):
    if varsta < 0:
        raise ValueError("Vârsta nu poate fi negativă!")
    return varsta

try:
    seteaza_varsta(-5)
except ValueError as eroare:
    print("Eroare:", eroare)
```

Output:

```
Eroare: Vârsta nu poate fi negativă!
```

---

# 5. `ZeroDivisionError` — Împărțire la Zero

## Exemplu 1 — Împărțire Simplă

```python
rezultat = 10 / 0
```

Output:

```
ZeroDivisionError: division by zero
```

## Exemplu 2 — Tratarea Erorii

```python
try:
    rezultat = 10 / 0
except ZeroDivisionError:
    print("Nu se poate împărți la zero!")
```

Output:

```
Nu se poate împărți la zero!
```

## Exemplu 3 — Împărțire Întreagă (`//`) la Zero

```python
rezultat = 10 // 0
```

Output:

```
ZeroDivisionError: integer division or modulo by zero
```

## Exemplu 4 — Restul Împărțirii (`%`) la Zero

```python
rezultat = 10 % 0
```

Output:

```
ZeroDivisionError: integer division or modulo by zero
```

## Exemplu 5 — Funcție Sigură de Împărțire

```python
def imparte(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Împărțirea la zero nu este permisă!"

print(imparte(10, 2))
print(imparte(10, 0))
```

Output:

```
5.0
Împărțirea la zero nu este permisă!
```

## Exemplu 6 — Calculator cu Input de la Utilizator

```python
try:
    a = float(input("Primul număr: "))
    b = float(input("Al doilea număr: "))
    print("Rezultat:", a / b)
except ZeroDivisionError:
    print("Nu poți împărți la zero!")
except ValueError:
    print("Trebuie să introduci numere valide!")
```

Exemplu de interacțiune:

```
Primul număr: 10
Al doilea număr: 0
Nu poți împărți la zero!
```

---

# 6. `IndexError` — Index în Afara Limitelor unei Liste

## Exemplu 1

```python
numere = [1, 2, 3]
print(numere[5])
```

Output:

```
IndexError: list index out of range
```

## Exemplu 2 — Tratarea Erorii

```python
numere = [1, 2, 3]

try:
    print(numere[5])
except IndexError:
    print("Nu există element la această poziție!")
```

Output:

```
Nu există element la această poziție!
```

## Exemplu 3 — Într-o Buclă, la Compararea Elementelor Vecine

```python
numere = [1, 2, 3]

for i in range(len(numere)):
    try:
        print(numere[i], "->", numere[i + 1])
    except IndexError:
        print(numere[i], "-> (nu mai există element următor)")
```

Output:

```
1 -> 2
2 -> 3
3 -> (nu mai există element următor)
```

---

# 7. `KeyError` — Cheie Inexistentă într-un Dicționar

## Exemplu 1

```python
student = {"nume": "Alice", "varsta": 20}
print(student["oras"])
```

Output:

```
KeyError: 'oras'
```

## Exemplu 2 — Tratarea Erorii

```python
student = {"nume": "Alice", "varsta": 20}

try:
    print(student["oras"])
except KeyError:
    print("Cheia 'oras' nu există în dicționar!")
```

Output:

```
Cheia 'oras' nu există în dicționar!
```

Explicație:

O alternativă la `try`/`except` pentru acest caz este `student.get("oras", "necunoscut")` (vezi [Dictionare.md](Dictionare.md)), care evită complet excepția.

---

# 8. `NameError` — Variabilă Nedefinită

## Exemplu 1

```python
print(varsta)
```

Output:

```
NameError: name 'varsta' is not defined
```

## Exemplu 2 — Tratarea Erorii

```python
try:
    print(varsta)
except NameError:
    print("Variabila 'varsta' nu a fost definită!")
```

Output:

```
Variabila 'varsta' nu a fost definită!
```

---

# 9. `AttributeError` — Metodă/Atribut Inexistent pentru un Tip

## Exemplu 1

```python
numar = 5
numar.append(3)
```

Output:

```
AttributeError: 'int' object has no attribute 'append'
```

Explicație:

`.append()` este o metodă a listelor, nu a numerelor întregi — `numar` este `int`, deci nu o poate folosi.

## Exemplu 2 — Tratarea Erorii

```python
text = "salut"

try:
    text.append("!")
except AttributeError:
    print("String-urile nu au metoda .append()!")
```

Output:

```
String-urile nu au metoda .append()!
```

---

# 10. `FileNotFoundError` — Fișier Inexistent

## Exemplu 1

```python
with open("nu_exista.txt", "r") as f:
    continut = f.read()
```

Output:

```
FileNotFoundError: [Errno 2] No such file or directory: 'nu_exista.txt'
```

## Exemplu 2 — Tratarea Erorii

```python
try:
    with open("nu_exista.txt", "r") as f:
        continut = f.read()
except FileNotFoundError:
    print("Fișierul nu a fost găsit!")
```

Output:

```
Fișierul nu a fost găsit!
```

---

# 11. Tratarea Mai Multor Tipuri de Excepții

## Exemplu 1 — Mai Multe Blocuri `except`

```python
try:
    a = int(input("Primul număr: "))
    b = int(input("Al doilea număr: "))
    print(a / b)
except ValueError:
    print("Trebuie să introduci numere întregi!")
except ZeroDivisionError:
    print("Nu poți împărți la zero!")
```

Exemplu de interacțiune:

```
Primul număr: 10
Al doilea număr: abc
Trebuie să introduci numere întregi!
```

## Exemplu 2 — Mai Multe Excepții în Același `except`

```python
try:
    numere = [1, 2, 3]
    print(numere[10])
except (IndexError, KeyError):
    print("Element sau cheie inexistentă!")
```

Output:

```
Element sau cheie inexistentă!
```

## Exemplu 3 — Prinderea Oricărei Excepții cu `Exception`

```python
try:
    rezultat = 10 / 0
except Exception as eroare:
    print("A apărut o eroare:", eroare)
```

Output:

```
A apărut o eroare: division by zero
```

Explicație:

`Exception` prinde **aproape orice** tip de eroare. E util ca ultimă plasă de siguranță, dar e recomandat să tratezi întâi excepțiile **specifice** (ex: `ValueError`, `ZeroDivisionError`), pentru mesaje mai clare.

---

# 12. `else` și `finally`

```python
try:
    numar = int(input("Introdu un număr: "))
except ValueError:
    print("Valoare invalidă!")
else:
    print("Ai introdus cu succes:", numar)
finally:
    print("Blocul try/except s-a terminat.")
```

Exemplu de interacțiune (fără eroare):

```
Introdu un număr: 7
Ai introdus cu succes: 7
Blocul try/except s-a terminat.
```

Exemplu de interacțiune (cu eroare):

```
Introdu un număr: abc
Valoare invalidă!
Blocul try/except s-a terminat.
```

Explicație:

* `else` se execută **doar dacă** nu a apărut nicio eroare în `try`
* `finally` se execută **întotdeauna**, indiferent dacă a apărut o eroare sau nu (util pentru curățenie, ex: închiderea unui fișier)

---

# 14. Rezumat

* O **excepție** este o eroare apărută la rulare, care oprește programul dacă nu e tratată
* `try` / `except` prinde eroarea și permite continuarea programului
* `TypeError` — operație pe un tip de date incompatibil (ex: `5 + "3"`)
* `ValueError` — tip corect, dar valoare invalidă (ex: `int("abc")`)
* `ZeroDivisionError` — împărțire la zero (`/`, `//`, `%`)
* `IndexError` — index în afara limitelor unei liste
* `KeyError` — cheie inexistentă într-un dicționar
* `NameError` — variabilă nedefinită
* `AttributeError` — metodă/atribut inexistent pentru tipul respectiv
* `FileNotFoundError` — fișier care nu există
* se pot trata mai multe excepții cu mai multe blocuri `except`, sau grupate `except (A, B)`
* `Exception` prinde aproape orice eroare — folosit ca plasă de siguranță
* `else` rulează dacă nu a fost nicio eroare; `finally` rulează întotdeauna
