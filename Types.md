# Python Theory: Types, Literals, Numeral Systems, and Operator Precedence

------------------------------------------------------------------------

# 1. Python Data Types

Python has several built‑in data types used to store and manipulate
data.

## 1.1 int (Integer)

Integers represent **whole numbers** without decimal points.

Examples:

``` python
a = 10
b = -25
c = 0
d = 999999
```

Arithmetic with integers:

``` python
x = 10
y = 3

print(x + y)   # 13
print(x - y)   # 7
print(x * y)   # 30
print(x // y)  # 3 (floor division)
print(x % y)   # 1 (remainder)
```

------------------------------------------------------------------------

## 1.2 float (Floating Point)

Floats represent **numbers with decimal values**.

``` python
price = 19.99
temperature = -5.4
pi = 3.141592
```

Example operations:

``` python
a = 5.5
b = 2.0

print(a + b)
print(a * b)
print(a / b)
```

------------------------------------------------------------------------

## 1.3 bool (Boolean)

Booleans represent **logical values**.

Possible values:

    True
    False

Examples:

``` python
is_online = True
is_admin = False
```

Boolean expressions:

``` python
print(5 > 3)     # True
print(10 == 7)   # False
print(4 != 2)    # True
```

Used in conditions:

``` python
age = 18

if age >= 18:
    print("Adult")
```

------------------------------------------------------------------------

## 1.4 list

Lists are **ordered, mutable collections**.

``` python
numbers = [1, 2, 3, 4]
names = ["Ana", "John", "Maria"]
mixed = [10, "hello", True, 3.5]
```

Accessing elements:

``` python
print(numbers[0])
print(numbers[2])
```

List modification:

``` python
numbers.append(5)
numbers.remove(2)
numbers[0] = 100
```

Loop example:

``` python
for n in numbers:
    print(n)
```

------------------------------------------------------------------------

## 1.5 tuple

Tuples are **ordered but immutable collections**.

``` python
point = (10, 20)
rgb = (255, 0, 0)
```

Access example:

``` python
print(point[0])
print(point[1])
```

Tuple unpacking:

``` python
x, y = point
print(x)
print(y)
```

------------------------------------------------------------------------

## 1.6 dict (Dictionary)

Dictionaries store **key‑value pairs**.

``` python
student = {
    "name": "Alice",
    "age": 20,
    "grade": "A"
}
```

Access values:

``` python
print(student["name"])
print(student["age"])
```

Modify values:

``` python
student["age"] = 21
student["city"] = "London"
```

Iterating through dictionary:

``` python
for key, value in student.items():
    print(key, value)
```

------------------------------------------------------------------------

# 2. Literals in Python

A **literal** is a fixed value written directly in the code.

Examples:

Numeric literals:

``` python
10
3.14
-7
```

String literals:

``` python
"Hello"
'Python'
```

Boolean literals:

``` python
True
False
```

Collection literals:

``` python
[1, 2, 3]
(4, 5, 6)
{"a": 1, "b": 2}
```

------------------------------------------------------------------------

# 3. Numeral Systems in Python

Numbers are usually written in the **decimal system (base 10)**.

Python also supports other numeral systems.

## Binary (base 2)

Prefix: **0b**

``` python
a = 0b1010
print(a)
```

Binary 1010 = Decimal 10

Example:

``` python
print(0b11 + 0b01)  # 4
```

------------------------------------------------------------------------

## Octal (base 8)

Prefix: **0o**

``` python
a = 0o12
print(a)
```

Octal 12 = Decimal 10

Example:

``` python
print(0o10)  # 8
```

------------------------------------------------------------------------

## Hexadecimal (base 16)

Prefix: **0x**

``` python
a = 0xA
print(a)
```

Hexadecimal A = Decimal 10

Example:

``` python
color = 0xFF
print(color)
```

------------------------------------------------------------------------

## Converting Between Systems

``` python
x = 10

print(bin(x))
print(oct(x))
print(hex(x))
```

Output:

    0b1010
    0o12
    0xa

------------------------------------------------------------------------

# 4. Operands and Operators

An **operand** is a value used by an operator.

Example:

``` python
5 + 3
```

-   5 → operand
-   3 → operand
-   -   → operator

Another example:

``` python
result = 10 * 2
```

Operands → 10, 2

Operator → \*

------------------------------------------------------------------------

# 5. Operator Precedence

Python evaluates expressions according to **precedence rules**.

Higher precedence operators are evaluated first.

## Precedence Order

  Operator                                  Description
  ----------------------------------------- ---------------------------------------------------
  ()                                        Parentheses
  \*\*                                      Exponentiation
  +x -x \~x                                 Unary plus, unary minus, bitwise NOT
  \* / // %                                 Multiplication, division, floor division, modulus
  \+ -                                      Addition and subtraction
  \<\< \>\>                                 Bitwise shifts
  &                                         Bitwise AND
  \^                                        Bitwise XOR
  \|                                        Bitwise OR
  == != \> \>= \< \<= is is not in not in   Comparisons
  not                                       Logical NOT
  and                                       Logical AND
  or                                        Logical OR

------------------------------------------------------------------------

# 6. Operator Examples

## Parentheses

``` python
print((2 + 3) * 4)
```

Result:

    20

------------------------------------------------------------------------

## Exponentiation

``` python
print(2 ** 3)
```

Result:

    8

------------------------------------------------------------------------

## Unary Operators

``` python
x = 5

print(-x)
print(+x)
```

------------------------------------------------------------------------

## Multiplication and Division

``` python
print(10 * 3)
print(10 / 3)
print(10 // 3)
print(10 % 3)
```

------------------------------------------------------------------------

## Addition and Subtraction

``` python
print(10 + 5)
print(10 - 5)
```

------------------------------------------------------------------------

## Bitwise Shift

``` python
print(5 << 1)
print(5 >> 1)
```

------------------------------------------------------------------------

## Bitwise AND

``` python
print(5 & 3)
```

------------------------------------------------------------------------

## Bitwise XOR

``` python
print(5 ^ 3)
```

------------------------------------------------------------------------

## Bitwise OR

``` python
print(5 | 3)
```

------------------------------------------------------------------------

## Comparisons

``` python
print(5 > 3)
print(5 == 5)
print(5 != 2)
```

------------------------------------------------------------------------

## Logical NOT

``` python
print(not True)
```

------------------------------------------------------------------------

## Logical AND

``` python
print(True and False)
```

------------------------------------------------------------------------

## Logical OR

``` python
print(True or False)
```

------------------------------------------------------------------------

# 7. Example of Full Precedence

``` python
result = 5 + 3 * 2 ** 2
print(result)
```

Step evaluation:

1.  Exponentiation → 2 \*\* 2 = 4
2.  Multiplication → 3 \* 4 = 12
3.  Addition → 5 + 12 = 17

Final result:

    17

------------------------------------------------------------------------

# 8. Summary

Python fundamentals include:

• Data types: int, float, bool, list, tuple, dict\
• Literals: fixed values written directly in code\
• Numeral systems: binary, octal, hexadecimal\
• Operands: values used in expressions\
• Operators: symbols performing operations\
• Operator precedence: determines evaluation order

Understanding these basics helps write **correct and predictable Python
programs**.
