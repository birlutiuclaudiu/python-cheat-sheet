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


----------------------------------------
# Python Expressions: Comprehensive Examples

## 1. Floor Division (`//`) Examples

### Example 1.1: Basic Floor Division
```python
result = 10 // 3
print(result)
```

Step-by-step:
1. `10 / 3 = 3.333...`
2. Floor division rounds down → `3`

**Result:** `3`

---

### Example 1.2: Floor Division with Negative Numbers
```python
result = -10 // 3
print(result)
```

Step-by-step:
1. `-10 / 3 = -3.333...`
2. Floor division rounds down (towards negative infinity) → `-4`

**Result:** `-4`

---

### Example 1.3: Floor Division with Floats
```python
result = 7.5 // 2.0
print(result)
```

Step-by-step:
1. `7.5 / 2.0 = 3.75`
2. Floor division rounds down → `3.0` (returns float)

**Result:** `3.0` (type: `float`)

---

## 2. Exponentiation (`**`) Examples

### Example 2.1: Basic Power Operation
```python
result = 2 ** 3
print(result)
```

Step-by-step:
1. `2 ** 3 = 2 × 2 × 2 = 8`

**Result:** `8`


## 3. Float Conversion in Mixed Operations

### Example 3.1: Integer + Float
```python
result = 5 + 2.5
print(result)
```

Step-by-step:
1. `5` (int) + `2.5` (float)
2. Result type follows float → convert to float

**Result:** `7.5` (type: `float`)

---

### Example 3.2: Division Always Returns Float
```python
result = 10 / 2
print(result)
```

Step-by-step:
1. Regular division `/` always returns float
2. `10 / 2 = 5.0`

**Result:** `5.0` (type: `float`)

---

### Example 3.3: Mixed Integer and Float Multiplication
```python
result = 3 * 2.4
print(result)
```

Step-by-step:
1. `3` (int) × `2.4` (float)
2. Result converts to float

**Result:** `7.2` (type: `float`)

---

## 4. Operator Precedence Examples

### Example 4.1: Power Before Multiplication
```python
result = 2 * 3 ** 2
print(result)
```

Step-by-step (left-to-right doesn't apply here):
1. `3 ** 2 = 9` (exponentiation first)
2. `2 * 9 = 18`

**Result:** `18`

**Rule:** `**` has higher precedence than `*`

---

### Example 4.2: Multiplication Before Addition
```python
result = 2 + 3 * 4
print(result)
```

Step-by-step:
1. `3 * 4 = 12` (multiplication first)
2. `2 + 12 = 14`

**Result:** `14`

**Rule:** `*` has higher precedence than `+`

---

### Example 4.3: Floor Division at Same Level as Division
```python
result = 20 / 4 // 2
print(result)
```

Step-by-step (left-to-right, same precedence):
1. `20 / 4 = 5.0` (left-to-right)
2. `5.0 // 2 = 2.0`

**Result:** `2.0` (type: `float`)

---

## 5. Complex Mixed Operations

### Example 5.1: Power + Floor Division + Addition
```python
result = 2 ** 3 + 10 // 4 - 1
print(result)
```

Step-by-step:
1. `2 ** 3 = 8` (exponentiation)
2. `10 // 4 = 2` (floor division)
3. `8 + 2 = 10` (addition, left-to-right)
4. `10 - 1 = 9` (subtraction)

**Result:** `9`

---

### Example 5.2: All Operators with Float Conversion
```python
result = 5.0 + 2 ** 2 * 3 // 2
print(result)
```

Step-by-step:
1. `2 ** 2 = 4` (exponentiation)
2. `4 * 3 = 12` (multiplication)
3. `12 // 2 = 6` (floor division)
4. `5.0 + 6 = 11.0` (addition with float → result is float)

**Result:** `11.0` (type: `float`)

---

### Example 5.3: Parentheses Override Precedence
```python
result = (2 + 3) ** 2
print(result)
```

Step-by-step:
1. `(2 + 3) = 5` (parentheses first)
2. `5 ** 2 = 25`

**Result:** `25`

---

### Example 5.4: Complex Expression with Multiple Float Operations
```python
result = (10 / 2 + 3) * 2 ** 2 // 3
print(result)
```

Step-by-step:
1. `10 / 2 = 5.0` (division)
2. `5.0 + 3 = 8.0` (addition in parentheses)
3. `2 ** 2 = 4` (exponentiation)
4. `8.0 * 4 = 32.0` (multiplication)
5. `32.0 // 3 = 10.0` (floor division with float → result is float)

**Result:** `10.0` (type: `float`)

---

## 6. Type Conversion with Explicit Casting

### Example 6.1: Converting Float to Int
```python
result = int(7.9) + 5
print(result)
```

Step-by-step:
1. `int(7.9) = 7` (truncates, doesn't round)
2. `7 + 5 = 12`

**Result:** `12`

---

### Example 6.2: Converting Int to Float
```python
result = float(5) / 2
print(result)
```

Step-by-step:
1. `float(5) = 5.0`
2. `5.0 / 2 = 2.5`

**Result:** `2.5` (type: `float`)

---

### Example 6.3: Mixed Casting and Operations
```python
result = int(3.7) ** 2 + float(5) / 2
print(result)
```

Step-by-step:
1. `int(3.7) = 3`
2. `3 ** 2 = 9`
3. `float(5) = 5.0`
4. `5.0 / 2 = 2.5`
5. `9 + 2.5 = 11.5`

**Result:** `11.5` (type: `float`)

---

## 7. Modulo (`%`) with Float Conversion

### Example 7.1: Modulo with Integers
```python
result = 10 % 3
print(result)
```

Step-by-step:
1. `10 / 3 = 3` remainder `1`
2. `10 % 3 = 1`

**Result:** `1`

---

### Example 7.2: Modulo in Complex Expression
```python
result = 10 % 3 + 2.5 * 2
print(result)
```

Step-by-step:
1. `10 % 3 = 1`
2. `2.5 * 2 = 5.0`
3. `1 + 5.0 = 6.0` (converts to float)

**Result:** `6.0` (type: `float`)

---

## 8. Operator Precedence Table (High to Low)

| Precedence | Operators | Description |
|---|---|---|
| 1 (Highest) | `**` | Exponentiation (right-to-left) |
| 2 | `+x`, `-x`, `~x` | Unary plus, minus, bitwise NOT |
| 3 | `*`, `/`, `//`, `%` | Multiplication, division, floor division, modulo (left-to-right) |
| 4 | `+`, `-` | Addition, subtraction (left-to-right) |

---

## 9. Key Takeaways

✅ **Float propagation**: If any operand is a float, the result is typically float
✅ **Floor division (`//`)**: Always rounds down (towards negative infinity)
✅ **True division (`/`)**: Always returns a float
✅ **Exponentiation (`**`)**: Higher precedence than `*` and `/`
✅ **Left-to-right**: Operators of same precedence are evaluated left-to-right (except `**`)
✅ **Parentheses**: Override any precedence rules

---

## 10. Practice Expressions

Try evaluating these before running them:

```python
# Challenge 1
result = 3 ** 2 - 2 * 4 + 1

# Challenge 2
result = 10 // 3 + 5.5 - 2

# Challenge 3
result = (8 + 2) / 2 ** 2 * 3

# Challenge 4
result = 2 ** 3 ** 2

# Challenge 5
result = 10 - 3 * 2 // 4 + 1.5
```

**Answers:**
- Challenge 1: `2` (9 - 8 + 1)
- Challenge 2: `6.5` (3 + 5.5 - 2)
- Challenge 3: `7.5` (10 / 4 * 3)
- Challenge 4: `512` (2 ** 9, right-to-left)
- Challenge 5: `10.5` (3 * 2 = 6, 6 // 4 = 1, then 10 - 1 + 1.5 = 10.5)