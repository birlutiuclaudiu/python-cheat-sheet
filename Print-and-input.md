# Python `print()` and `input()` — Definition and Examples

This document explains the **`print()`** and **`input()`** functions in Python, including definitions and practical examples.

---

# 1. The `print()` Function

## Definition

`print()` is a built-in Python function used to **display output to the console**.

It can print:

* text
* numbers
* variables
* results of expressions
* multiple values at once

Basic syntax:

```python
print(value1, value2, ...)
```

---

## Example 1 — Printing Text

```python
print("Hello, world!")
```

Output:

```
Hello, world!
```

Explanation:

The text inside quotation marks is called a **string literal**, and `print()` displays it.

---

## Example 2 — Printing Numbers

```python
print(10)
print(3.14)
```

Output:

```
10
3.14
```

Explanation:

`print()` can display numeric values directly.

---

## Example 3 — Printing Variables

```python
name = "Alice"
age = 20

print(name)
print(age)
```

Output:

```
Alice
20
```

Explanation:

The function prints the **values stored in the variables**.

---

## Example 4 — Printing Multiple Values

```python
name = "John"
age = 25

print("Name:", name, "Age:", age)
```

Output:

```
Name: John Age: 25
```

Explanation:

`print()` automatically adds a **space between values** separated by commas.

---

## Example 5 — Printing an Expression

```python
print(5 + 3)
print(10 * 2)
```

Output:

```
8
20
```

Explanation:

Python **evaluates the expression first**, then prints the result.

---

## Example 6 — Custom Separator

```python
print("Python", "Java", "C++", sep=" | ")
```

Output:

```
Python | Java | C++
```

Explanation:

The `sep` parameter changes the **separator between printed values**.

---

## Example 7 — Custom End Character

```python
print("Hello", end=" ")
print("World")
```

Output:

```
Hello World
```

Explanation:

By default, `print()` ends with a **newline**.
Using `end=" "` changes what is printed at the end.

---

# 2. The `input()` Function

## Definition

`input()` is a built-in Python function used to **read input from the user via the keyboard**.

It pauses the program and waits for the user to type something.

Basic syntax:

```python
input("message")
```

The function **always returns a string**.

---

## Example 1 — Simple Input

```python
name = input("Enter your name: ")
print(name)
```

Example interaction:

```
Enter your name: Alice
Alice
```

Explanation:

The text entered by the user is stored in the variable `name`.

---

## Example 2 — Greeting the User

```python
name = input("Enter your name: ")

print("Hello,", name)
```

Example:

```
Enter your name: Maria
Hello, Maria
```

---

## Example 3 — Input with Numbers

```python
age = input("Enter your age: ")

print("You are", age, "years old")
```

Example:

```
Enter your age: 21
You are 21 years old
```

Explanation:

Even though the user enters a number, the result is still a **string**.

---

# 3. Converting Input to Numbers

Since `input()` returns a **string**, you must convert it if you want to perform calculations.

---

## Example 1 — Converting to Integer

```python
age = int(input("Enter your age: "))

print(age + 5)
```

Example:

```
Enter your age: 20
25
```

Explanation:

`int()` converts the input from **string to integer**.

---

## Example 2 — Converting to Float

```python
price = float(input("Enter the price: "))

print(price * 2)
```

Example:

```
Enter the price: 5.5
11.0
```

Explanation:

`float()` converts the input into a **decimal number**.

---

# 4. Multiple Inputs

You can ask for multiple values from the user.

---

## Example — Two Numbers

```python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))

print("Sum:", a + b)
```

Example:

```
Enter first number: 5
Enter second number: 3
Sum: 8
```

Explanation:

Each input is converted to an integer so mathematical operations can be performed.

---

# 5. Combining `print()` and `input()`

Example program:

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

print("Hello", name)
print("Next year you will be", age + 1)
```

Example interaction:

```
Enter your name: Alex
Enter your age: 22
Hello Alex
Next year you will be 23
```

---

# 6. Summary

**`print()`**

* Displays output to the console
* Can print text, numbers, variables, and expressions
* Supports parameters like `sep` and `end`

**`input()`**

* Reads input from the user
* Always returns a **string**
* Often combined with `int()` or `float()` for calculations

These functions are essential for creating **interactive Python programs**.
