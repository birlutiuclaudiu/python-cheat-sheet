# Biți în Python — Conversie în Baza 2 și Operații (Numere Pozitive)

Acest document explică cum se convertesc numerele între baza 10 și baza 2, și cum funcționează operațiile pe biți (`&`, `|`, `^`, `~`) în Python.

---

# 1. Conversie din Baza 10 în Baza 2 — Algoritm cu Rest

Se împarte numărul repetat la 2, se rețin resturile, iar rezultatul se citește de la ultimul rest către primul.

Exemplu: `13` → baza 2

```
13 / 2 = 6  rest 1
 6 / 2 = 3  rest 0
 3 / 2 = 1  rest 1
 1 / 2 = 0  rest 1
```

Citim resturile de jos în sus: `1101` → `13 = 1101` (baza 2)

```python
def in_baza_2(n):
    if n == 0:
        return "0"
    rezultat = ""
    while n > 0:
        rest = n % 2
        rezultat = str(rest) + rezultat   # adăugăm la început
        n = n // 2
    return rezultat

print(in_baza_2(13))     # 1101
print(bin(13))           # 0b1101  (varianta built-in din Python, pentru verificare)
```

---

# 2. Conversie din Baza 2 în Baza 10 — Algoritm

Fiecare cifră binară se înmulțește cu puterea lui 2 corespunzătoare poziției ei (numărată de la dreapta la stânga, începând de la 0), apoi se adună toate.

Exemplu: `1101` (baza 2) → baza 10

```
poziții (de la dreapta):   3 2 1 0
cifre:                     1 1 0 1

1*2^3 + 1*2^2 + 0*2^1 + 1*2^0
= 1*8 + 1*4 + 0*2 + 1*1
= 8 + 4 + 0 + 1
= 13
```

```python
def in_baza_10(binar):
    rezultat = 0
    putere = 0
    for cifra in reversed(binar):     # parcurgem string-ul de la dreapta la stânga
        rezultat += int(cifra) * (2 ** putere)
        putere += 1
    return rezultat

print(in_baza_10("1101"))    # 13
print(int("1101", 2))        # 13  (varianta built-in din Python, pentru verificare)
```

---

# 3. Operații pe Biți (Numere Pozitive, până la 64)

## Exemplu 1

```python
a = 12   # 0001100
b = 10   # 0001010
```

### AND (`&`) — 1 doar dacă ambii biți sunt 1

```python
print(a & b)    # 1100 & 1010 = 1000 -> 8
```

### OR (`|`) — 1 dacă cel puțin un bit este 1

```python
print(a | b)    # 1100 | 1010 = 1110 -> 14
```

### XOR / SAU EXCLUSIV (`^`) — 1 dacă biții sunt diferiți

```python
print(a ^ b)    # 1100 ^ 1010 = 0110 -> 6
```

### NOT (`~`) — Inversează Toți Biții

`~n` este echivalent cu `-(n+1)`.

```python
print(~a)       # ~12 -> -13
```

---

## Exemplu 2 — Numere Mai Mari

```python
x = 45   # 0101101
y = 58   # 0111010

print(bin(x))     # 0b101101
print(bin(y))     # 0b111010
```

### AND

```python
rezultat_and = x & y
print(rezultat_and)            # 101101 & 111010 = 101000 -> 40
print(bin(rezultat_and))       # 0b101000
# verificare conversie manuală: 101000 -> 1*32 + 0*16 + 1*8 + 0*4 + 0*2 + 0*1 = 32+8 = 40
```

### OR

```python
rezultat_or = x | y
print(rezultat_or)             # 101101 | 111010 = 111111 -> 63
print(bin(rezultat_or))        # 0b111111
# verificare: 111111 -> 32+16+8+4+2+1 = 63
```

### XOR

```python
rezultat_xor = x ^ y
print(rezultat_xor)            # 101101 ^ 111010 = 010111 -> 23
print(bin(rezultat_xor))       # 0b10111
# verificare: 010111 -> 16+0+4+2+1 = 23
```

### NOT

```python
print(~x)                      # ~45 -> -(45+1) = -46
```

---

## Exemplu 3 — Numărul 64 și Operații cu El

```python
n = 64    # 1000000

print(bin(n))           # 0b1000000
print(n & 12)           # 1000000 & 0001100 = 0000000 -> 0  (nu au niciun bit comun setat)
print(n | 12)           # 1000000 | 0001100 = 1001100 -> 76
# verificare: 1001100 -> 64+8+4 = 76
print(n ^ 12)            # 1000000 ^ 0001100 = 1001100 -> 76 (același rezultat ca OR, pentru că n și 12 nu au biți comuni)
print(~n)                # ~64 -> -(64+1) = -65
```

---

# 4. Rezumat

* **Baza 10 → Baza 2:** împărțiri repetate la 2, resturile citite de jos în sus
* **Baza 2 → Baza 10:** fiecare cifră × puterea lui 2 corespunzătoare poziției, apoi se adună
* `bin(n)` și `int(text, 2)` sunt funcțiile built-in echivalente algoritmilor de mai sus

| Operator | Nume | Rezultat |
|----------|------|----------|
| `&`  | AND | 1 doar dacă ambii biți sunt 1 |
| `\|` | OR  | 1 dacă cel puțin un bit este 1 |
| `^`  | XOR | 1 dacă biții sunt diferiți |
| `~`  | NOT | inversează toți biții (`~n == -(n+1)`) |
