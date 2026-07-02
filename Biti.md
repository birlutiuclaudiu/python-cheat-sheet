# Biți în Python — Conversie în Baza 2 și Operații (Numere Pozitive)

Acest document explică cum se convertesc numerele între baza 10 și baza 2, și cum funcționează operațiile pe biți (`&`, `|`, `^`, `~`, `<<`, `>>`) în Python.

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

### LEFT SHIFT (`<<`) — Deplasează Biții la Stânga

`n << k` mută toți biții lui `n` cu `k` poziții spre stânga, completând cu `0` în dreapta. Este echivalent cu **`n * 2^k`**.

```python
print(a << 2)   # 0001100 << 2 = 0110000 -> 48   (12 * 2^2 = 48)
print(b << 1)   # 0001010 << 1 = 0010100 -> 20   (10 * 2^1 = 20)
```

### RIGHT SHIFT (`>>`) — Deplasează Biții la Dreapta

`n >> k` mută toți biții lui `n` cu `k` poziții spre dreapta, eliminând biții din capătul din dreapta. Pentru numere pozitive, este echivalent cu **împărțire întreagă `n // 2^k`**.

```python
print(a >> 2)   # 0001100 >> 2 = 0000011 -> 3    (12 // 2^2 = 3)
print(b >> 1)   # 0001010 >> 1 = 0000101 -> 5    (10 // 2^1 = 5)
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

### LEFT SHIFT (`<<`)

```python
rezultat_shl = x << 1
print(rezultat_shl)            # 0101101 << 1 = 1011010 -> 90   (45 * 2 = 90)
print(bin(rezultat_shl))       # 0b1011010

rezultat_shl2 = y << 2
print(rezultat_shl2)           # 0111010 << 2 = 11101000 -> 232 (58 * 4 = 232)
```

### RIGHT SHIFT (`>>`)

```python
rezultat_shr = x >> 1
print(rezultat_shr)            # 0101101 >> 1 = 0010110 -> 22   (45 // 2 = 22, bitul de 1 se pierde)
print(bin(rezultat_shr))       # 0b10110

rezultat_shr2 = y >> 3
print(rezultat_shr2)           # 0111010 >> 3 = 0000111 -> 7    (58 // 8 = 7)
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
print(n << 1)             # 1000000 << 1 = 10000000 -> 128 (64 * 2 = 128)
print(n >> 6)             # 1000000 >> 6 = 0000001 -> 1    (64 // 64 = 1)
print(n >> 7)             # 1000000 >> 7 = 0000000 -> 0    (bitul de 1 iese complet din număr)
```

---

# 4. Operatorii de Shift (`<<` și `>>`) — Explicație Detaliată

| Operator | Nume | Efect | Echivalent aritmetic (numere pozitive) |
|---|---|---|---|
| `n << k` | Left shift | mută biții spre stânga cu `k` poziții, completează cu `0` în dreapta | `n * 2^k` |
| `n >> k` | Right shift | mută biții spre dreapta cu `k` poziții, elimină biții din dreapta | `n // 2^k` (împărțire întreagă) |

## Observații importante

* **`<<` dublează valoarea** la fiecare poziție deplasată: `n << 1` = `n * 2`, `n << 2` = `n * 4`, `n << 3` = `n * 8` etc.
* **`>>` înjumătățește valoarea** (rotunjit în jos) la fiecare poziție: `n >> 1` = `n // 2`, `n >> 2` = `n // 4` etc.
* La `>>`, biții care "ies" din capătul din dreapta sunt **pierduți definitiv** — de aceea rezultatul este o împărțire întreagă, nu una exactă.
* Ambii operatori funcționează doar cu numere **întregi**; `k` (numărul de poziții) trebuie să fie un întreg **≥ 0**, altfel Python aruncă `ValueError: negative shift count`.

```python
print(5 << -1)   # ValueError: negative shift count
```

* Deplasarea peste toți biții semnificativi ai unui număr pozitiv duce la `0` la `>>`, respectiv la un număr foarte mare la `<<` (Python nu are limită fixă de biți pentru `int`, spre deosebire de alte limbaje).

```python
print(1 >> 5)     # 0   (bitul unic iese din număr)
print(1 << 5)     # 32  (1 * 2^5)
```

---

# 5. Rezumat

* **Baza 10 → Baza 2:** împărțiri repetate la 2, resturile citite de jos în sus
* **Baza 2 → Baza 10:** fiecare cifră × puterea lui 2 corespunzătoare poziției, apoi se adună
* `bin(n)` și `int(text, 2)` sunt funcțiile built-in echivalente algoritmilor de mai sus

| Operator | Nume | Rezultat |
|----------|------|----------|
| `&`  | AND | 1 doar dacă ambii biți sunt 1 |
| `\|` | OR  | 1 dacă cel puțin un bit este 1 |
| `^`  | XOR | 1 dacă biții sunt diferiți |
| `~`  | NOT | inversează toți biții (`~n == -(n+1)`) |
| `<<` | Left shift | deplasează biții la stânga, echivalent `n * 2^k` |
| `>>` | Right shift | deplasează biții la dreapta, echivalent `n // 2^k` |