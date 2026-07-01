# Fișiere în Python — Moduri de Deschidere, Scriere, Citire

Acest document explică modurile de deschidere a fișierelor în Python (`r`, `w`, `a`, `r+`, `w+`, `a+`) și modurile de scriere/citire, cu exemple pentru fiecare.

---

# 1. Moduri de Deschidere

Cursorul ("file pointer") este poziția din fișier de la care se va citi/scrie următorul caracter/byte. Fiecare mod îl poziționează diferit la deschidere.

## `'r'` (read)

* fișierul **trebuie** să existe, altfel eroare (`FileNotFoundError`)
* cursorul se poziționează la **începutul** fișierului
* doar citire permisă, scrierea dă eroare

## `'w'` (write)

* dacă fișierul există, **șterge** tot conținutul (truncate) la deschidere
* dacă nu există, îl creează
* cursorul se poziționează la începutul fișierului (care e gol acum)
* doar scriere permisă, citirea dă eroare

## `'a'` (append)

* dacă fișierul există, conținutul rămâne intact
* dacă nu există, îl creează
* cursorul se poziționează la **finalul** fișierului
* doar scriere permisă; tot ce scrii se adaugă **după** conținutul existent
* chiar dacă faci `f.seek(0)` ca să muți cursorul, la scriere Python îl trimite automat înapoi la final (comportament specific modului `'a'`)

## `'r+'` (read + write)

* fișierul **trebuie** să existe
* cursorul se poziționează la început
* permite **și** citire **și** scriere
* scrierea se face peste conținutul existent, de la poziția cursorului (suprascrie caracter cu caracter, **nu** inserează, **nu** șterge restul automat)

## `'w+'` (write + read)

* șterge conținutul existent (ca la `'w'`), sau creează fișier nou
* cursorul la început (al unui fișier gol)
* permite **și** citire **și** scriere (dar imediat după `'w+'` nu e nimic de citit, pentru că fișierul a fost golit)

## `'a+'` (append + read)

* conținutul existent rămâne intact, sau creează fișier nou
* cursorul de **scriere** e mereu la final (ca la `'a'`)
* cursorul de **citire** poate fi mutat cu `f.seek()` ca să citești de oriunde, dar orice scriere ulterioară merge tot la finalul fișierului

---

# 2. Exemple Practice

## `r+` — Citim, Mutăm Cursorul, Scriem Peste

```python
with open('fisier.txt', 'r+', encoding='utf-8') as f:
    continut = f.read()        # citește tot, cursorul ajunge la final
    f.seek(0)                  # mutăm cursorul înapoi la început
    f.write('NOU')             # suprascrie primele 3 caractere existente
```

## `a+` — Citim Ce E Deja Scris, Apoi Adăugăm

```python
with open('fisier.txt', 'a+', encoding='utf-8') as f:
    f.seek(0)                  # mutăm cursorul de citire la început
    print(f.read())             # citim tot conținutul existent
    f.write('linie noua\n')    # scrierea se face la final, indiferent de seek
```

---

# 3. Varianta Simplă, Fără `with open`

Diferența: trebuie să închizi manual fișierul cu `f.close()`.

Riscul: dacă apare o eroare între `open()` și `close()`, fișierul poate rămâne deschis (de aceea `with` e recomandat în practică).

```python
f = open('fisier.txt', 'r+', encoding='utf-8')
continut = f.read()
f.seek(0)
f.write('NOU')
f.close()                      # obligatoriu, altfel fișierul rămâne deschis

f = open('fisier.txt', 'a+', encoding='utf-8')
f.seek(0)
print(f.read())
f.write('linie noua\n')
f.close()
```

---

# 4. Scriere

```python
with open('output.txt', 'w', encoding='utf-8') as f:
    f.write('prima linie\n')
    f.write('a doua linie\n')
```

Varianta fără `with`:

```python
f = open('output.txt', 'w', encoding='utf-8')
f.write('prima linie\n')
f.write('a doua linie\n')
f.close()
```

---

# 5. Adăugare (Append) la Finalul unui Fișier Existent

```python
with open('output.txt', 'a', encoding='utf-8') as f:
    f.write('linie adăugată\n')
```

Varianta fără `with`:

```python
f = open('output.txt', 'a', encoding='utf-8')
f.write('linie adăugată\n')
f.close()
```

---

# 6. Citire Caracter cu Caracter

```python
with open('output.txt', 'r', encoding='utf-8') as f:
    caracter = f.read(1)               # citește 1 caracter
    while caracter:
        print(caracter, end='')
        caracter = f.read(1)
```

Varianta fără `with`:

```python
f = open('output.txt', 'r', encoding='utf-8')
caracter = f.read(1)
while caracter:
    print(caracter, end='')
    caracter = f.read(1)
f.close()
```

---

# 7. Citire Linie cu Linie

```python
with open('output.txt', 'r', encoding='utf-8') as f:
    for linie in f:                    # eficient, nu încarcă tot fișierul în memorie
        print(linie.strip())           # .strip() elimină \n de la final
```

Varianta fără `with`:

```python
f = open('output.txt', 'r', encoding='utf-8')
for linie in f:
    print(linie.strip())
f.close()
```

## Alternativ — Citirea Tuturor Liniilor într-o Listă

```python
with open('output.txt', 'r', encoding='utf-8') as f:
    linii = f.readlines()              # listă de string-uri
```

Varianta fără `with`:

```python
f = open('output.txt', 'r', encoding='utf-8')
linii = f.readlines()
f.close()
```

---

# 8. Rezumat

| Mod   | Fișier trebuie să existe | Șterge conținutul | Poziția cursorului | Citire | Scriere |
|-------|:-------------------------:|:------------------:|---------------------|:------:|:-------:|
| `r`   | Da                         | Nu                  | Început              | Da     | Nu      |
| `w`   | Nu                         | Da                  | Început              | Nu     | Da      |
| `a`   | Nu                         | Nu                  | Final                | Nu     | Da      |
| `r+`  | Da                         | Nu                  | Început              | Da     | Da      |
| `w+`  | Nu                         | Da                  | Început              | Da     | Da      |
| `a+`  | Nu                         | Nu                  | Final (la scriere)   | Da     | Da      |

* Folosește `with open(...)` — închide fișierul automat, chiar dacă apare o eroare.
* `f.seek(0)` mută cursorul înapoi la început, dar la modul `'a'`/`'a+'` scrierea merge oricum la final.
* Citirea se poate face caracter cu caracter (`f.read(1)`), linie cu linie (`for linie in f`) sau toate liniile odată (`f.readlines()`).
