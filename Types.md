# Python Basics: Types, Literals, and Operator Order

## 1. Python Data Types

Python has several built-in data types used to store values. Some of the
most common are:

### int (Integer)

-   Represents whole numbers (positive or negative) without decimals.
-   Examples:

``` python
x = 10
y = -5
z = 0
```

### float (Floating Point)

-   Represents numbers with decimal points.
-   Examples:

``` python
price = 9.99
temperature = -3.5
pi = 3.14159
```

### bool (Boolean)

-   Represents logical values: `True` or `False`.
-   Often used in conditions.

``` python
is_active = True
is_logged_in = False
```

### list

-   An ordered and **mutable** (changeable) collection.
-   Allows duplicate elements.

``` python
numbers = [1, 2, 3, 4]
names = ["Ana", "John", "Maria"]
mixed = [1, "hello", True]
```

Common list operations:

``` python
numbers.append(5)
numbers.remove(2)
print(numbers[0])
```

### tuple

-   An ordered but **immutable** (cannot be changed) collection.

``` python
coordinates = (10, 20)
rgb = (255, 0, 0)
```

You cannot modify a tuple after creation.

### dict (Dictionary)

-   Stores data as **key-value pairs**.

``` python
student = {
    "name": "Alice",
    "age": 20,
    "grade": "A"
}
```

Accessing values:

``` python
print(student["name"])
student["age"] = 21
```

------------------------------------------------------------------------

# 2. Literals in Python

A **literal** is a fixed value written directly in the code.

Examples:

### Numeric Literals

``` python
10      # int literal
3.14    # float literal
```

### String Literals

``` python
"Hello"
'Python'
```

### Boolean Literals

``` python
True
False
```

### Collection Literals

``` python
[1, 2, 3]              # list literal
(4, 5, 6)              # tuple literal
{"a": 1, "b": 2}       # dict literal
```

------------------------------------------------------------------------

# 3. Operands and Operators

An **operand** is a value that operators act on.

Example:

``` python
5 + 3
```

-   `5` → operand
-   `3` → operand
-   `+` → operator

Operators perform operations such as:

-   arithmetic
-   comparison
-   logical operations

------------------------------------------------------------------------

# 4. Operator Precedence (Order of Operations)

Python evaluates expressions based on **operator precedence**.

From **highest priority to lowest**:

  Priority   Operators           Description
  ---------- ------------------- --------------------------------------------------
  1          `()`                Parentheses
  2          `**`                Exponent
  3          `* / // %`          Multiplication, division, floor division, modulo
  4          `+ -`               Addition, subtraction
  5          `== != > < >= <=`   Comparisons
  6          `not`               Logical NOT
  7          `and`               Logical AND
  8          `or`                Logical OR

Example:

``` python
result = 5 + 3 * 2
print(result)
```

Python first calculates:

    3 * 2 = 6
    5 + 6 = 11

If we want a different order:

``` python
result = (5 + 3) * 2
print(result)  # 16
```

------------------------------------------------------------------------

# 5. Summary

-   **int, float, bool** → basic primitive types
-   **list, tuple, dict** → collection data types
-   **literals** → fixed values written in code
-   **operands** → values used by operators
-   **operator precedence** → determines evaluation order

Understanding these fundamentals is essential for writing correct Python
programs.
