# Python Examples: Operator Precedence, `//` Operator, and Type Conversion

This document contains **examples and explanations** of:
- Operator precedence
- The floor division operator `//`
- Type conversion (casting)

---

# 1. Operator Precedence Examples

Operator precedence determines **which operation Python executes first** in an expression.

Operators with **higher precedence** are evaluated before lower ones.

---

## Example 1 — Multiplication before Addition

```python
result = 5 + 3 * 2
print(result)
```

Step-by-step evaluation:

1. `3 * 2 = 6`
2. `5 + 6 = 11`

Result:

```
11
```

Explanation:

Multiplication `*` has **higher precedence** than addition `+`.

---

## Example 2 — Using Parentheses

```python
result = (5 + 3) * 2
print(result)
```

Steps:

1. `(5 + 3) = 8`
2. `8 * 2 = 16`

Result:

```
16
```

Explanation:

Parentheses `()` **override normal precedence** and force Python to evaluate that expression first.

---

## Example 3 — Exponentiation

```python
result = 2 * 3 ** 2
print(result)
```

Steps:

1. `3 ** 2 = 9`
2. `2 * 9 = 18`

Result:

```
18
```

Explanation:

Exponentiation `**` has **higher precedence than multiplication**.

---

## Example 4 — Multiple Operators

```python
result = 10 + 6 / 2 * 3
print(result)
```

Steps:

1. `6 / 2 = 3`
2. `3 * 3 = 9`
3. `10 + 9 = 19`

Result:

```
19
```

Explanation:

Division `/` and multiplication `*` have the **same precedence**, so they are evaluated **left to right**.

---

## Example 5 — Complex Expression

```python
result = 5 + 3 * 2 ** 2
print(result)
```

Steps:

1. `2 ** 2 = 4`
2. `3 * 4 = 12`
3. `5 + 12 = 17`

Result:

```
17
```

---

# 2. Floor Division Operator `//`

The `//` operator performs **floor division**.

It divides two numbers and **rounds the result down to the nearest integer**.

---

## Example 1 — Basic Floor Division

```python
print(10 // 3)
```

Normal division:

```
10 / 3 = 3.333...
```

Floor division result:

```
3
```

Explanation:

The decimal part is **discarded**, and the value is rounded **down**.

---

## Example 2 — Floor Division with Floats

```python
print(10.0 // 3)
```

Result:

```
3.0
```

Explanation:

If one operand is a **float**, the result will also be a **float**.

---

## Example 3 — Negative Numbers

```python
print(-10 // 3)
```

Result:

```
-4
```

Explanation:

Floor division always rounds **toward negative infinity**, not toward zero.

```
-10 / 3 = -3.333...
floor → -4
```

---

## Example 4 — Using `//` in an Expression

```python
result = 20 // 6 + 2
print(result)
```

Steps:

1. `20 // 6 = 3`
2. `3 + 2 = 5`

Result:

```
5
```

---

# 3. Type Conversion (Casting)

Type conversion changes a value from **one data type to another**.

Python provides built-in functions:

- `int()`
- `float()`
- `str()`
- `bool()`

---

## Example 1 — Float to Integer

```python
x = 5.9
y = int(x)

print(y)
```

Result:

```
5
```

Explanation:

`int()` **removes the decimal part** (it does not round).

---

## Example 2 — Integer to Float

```python
x = 7
y = float(x)

print(y)
```

Result:

```
7.0
```

Explanation:

The integer becomes a **floating-point number**.

---

## Example 3 — Integer to String

```python
age = 20
text = "Age: " + str(age)

print(text)
```

Result:

```
Age: 20
```

Explanation:

Strings cannot be concatenated with integers, so `str()` converts the number.

---

## Example 4 — String to Integer

```python
num = "50"
value = int(num)

print(value + 10)
```

Result:

```
60
```

Explanation:

The string `"50"` is converted into the integer `50`.

---

## Example 5 — String to Float

```python
price = "19.99"
value = float(price)

print(value * 2)
```

Result:

```
39.98
```

Explanation:

The string becomes a floating-point number so arithmetic can be performed.

---

## Example 6 — Boolean Conversion

```python
print(bool(1))
print(bool(0))
print(bool("hello"))
print(bool(""))
```

Results:

```
True
False
True
False
```

Explanation:

Python treats the following as **False**:

- `0`
- `""` (empty string)
- `None`
- empty collections (`[]`, `{}`, `()`)

Most other values are **True**.

---

# 4. Combined Example (Precedence + Floor Division + Conversion)

```python
result = int(5.8) + 10 // 3 * 2
print(result)
```

Step-by-step evaluation:

1. `int(5.8) → 5`
2. `10 // 3 → 3`
3. `3 * 2 → 6`
4. `5 + 6 → 11`

Result:

```
11
```

Explanation:

This example combines:

- **Type conversion (`int()`)**
- **Floor division (`//`)**
- **Operator precedence**