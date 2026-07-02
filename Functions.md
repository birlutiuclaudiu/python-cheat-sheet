# Python Functions — Definition, Parameters, and Examples

This document explains **functions** in Python: what they are, how to define them, how to call them, and how parameters and arguments work — with practical examples for each case.

---

# 1. What Is a Function?

A **function** is a named, reusable block of code that performs a specific task.

Functions help you:

* avoid repeating the same code
* organize a program into smaller, readable pieces
* reuse logic by calling it whenever needed

Python has:

* **Built-in functions** — already provided by Python (e.g. `print()`, `input()`, `len()`)
* **User-defined functions** — functions you create yourself using the `def` keyword

---

# 2. Defining a Function

Basic syntax:

```python
def function_name(parameters):
    # function body
    return value
```

* `def` — keyword that starts a function definition
* `function_name` — the name used to call the function
* `parameters` — optional input values the function accepts (in parentheses)
* `:` — marks the start of the function body
* the function body must be **indented**
* `return` — optional; sends a value back to the caller

---

## Example 1 — A Simple Function

```python
def greet():
    print("Hello!")
```

Defining the function does **not** run it. You must **call** it:

```python
greet()
```

Output:

```
Hello!
```

Explanation:

`greet` is the function name, `()` means it takes no parameters, and `greet()` is how you **call** (execute) it.

---

# 3. Calling a Function

To call (run) a function, write its name followed by parentheses `()`, with any required arguments inside.

```python
def say_hello():
    print("Hi there!")

say_hello()   # calling the function
say_hello()   # can be called multiple times
```

Output:

```
Hi there!
Hi there!
```

Explanation:

A function can be called as many times as needed, from anywhere after it has been defined.

---

# 4. Parameters and Arguments

* A **parameter** is the name listed in the function definition.
* An **argument** is the actual value passed when calling the function.

```python
def greet(name):   # "name" is a parameter
    print("Hello,", name)

greet("Alice")     # "Alice" is an argument
```

Output:

```
Hello, Alice
```

---

## Example 1 — One Parameter

```python
def greet(name):
    print("Hello,", name)

greet("Maria")
greet("John")
```

Output:

```
Hello, Maria
Hello, John
```

Explanation:

Each call passes a different **argument**, so `name` holds a different value each time.

---

## Example 2 — Multiple Parameters

```python
def add(a, b):
    print(a + b)

add(5, 3)
add(10, 20)
```

Output:

```
8
30
```

Explanation:

Arguments are matched to parameters **in order**: `a = 5`, `b = 3` for the first call.

---

## Example 3 — Default Parameter Values

```python
def greet(name="Guest"):
    print("Hello,", name)

greet("Alice")
greet()
```

Output:

```
Hello, Alice
Hello, Guest
```

Explanation:

If a parameter has a **default value**, the argument becomes optional. When it's not provided, the default is used.

---

## Example 4 — Keyword Arguments

```python
def student_info(name, age):
    print(name, "is", age, "years old")

student_info(age=20, name="John")
```

Output:

```
John is 20 years old
```

Explanation:

With **keyword arguments**, you specify which parameter each value belongs to, so the order no longer matters.

---


# 5. The `return` Statement

`return` sends a value back to the place where the function was called, so it can be stored or used.

```python
def square(x):
    return x * x

result = square(4)
print(result)
```

Output:

```
16
```

Explanation:

Unlike `print()`, which only displays a value, `return` gives the value back so it can be **used later in the program**.

---

## Example 1 — Function Without `return`

```python
def greet(name):
    print("Hello,", name)

result = greet("Alice")
print(result)
```

Output:

```
Hello, Alice
None
```

Explanation:

If a function has no `return` statement, it returns `None` by default.

---

## Example 2 — Returning Multiple Values

```python
def min_max(numbers):
    return min(numbers), max(numbers)

low, high = min_max([4, 1, 9, 2])
print(low, high)
```

Output:

```
1 9
```

Explanation:

Python allows returning **multiple values** as a tuple, which can be unpacked into separate variables.

---

## Example 3 — Using the Return Value in an Expression

```python
def double(x):
    return x * 2

print(double(5) + 1)
```

Output:

```
11
```

Explanation:

Because `double(5)` returns `10`, the expression becomes `10 + 1`.

---

# 6. Combining Parameters, Defaults, and Return

```python
def calculate_price(price, discount=0):
    final_price = price - (price * discount / 100)
    return final_price

print(calculate_price(100))
print(calculate_price(100, 20))
```

Output:

```
100.0
80.0
```

Explanation:

`discount` has a default value of `0`, so it's optional. When provided, it changes the calculation.

---

# 7. Docstrings

A **docstring** is a short description placed right after the `def` line, explaining what the function does.

```python
def add(a, b):
    """Return the sum of a and b."""
    return a + b

print(add.__doc__)
```

Output:

```
Return the sum of a and b.
```

Explanation:

Docstrings document a function's purpose and can be viewed with `help(function_name)` or `function_name.__doc__`.

---

# 8. Variable Scope

A variable created **inside** a function is **local** — it only exists while the function runs and cannot be used outside it.

```python
def show_message():
    message = "Hi!"
    print(message)

show_message()
print(message)   # Error: message is not defined here
```

Output:

```
Hi!
Traceback (most recent call last):
NameError: name 'message' is not defined
```

Explanation:

`message` is **local** to `show_message()`, so it does not exist outside the function.

---

# 9. Summary

**Defining a function**

```python
def function_name(parameters):
    return value
```

**Key ideas**

* A function is defined once with `def` and can be **called** many times
* **Parameters** are placeholders; **arguments** are the actual values passed in
* Parameters can have **default values**, making them optional
* **Keyword arguments** let you pass values by name, in any order
* `return` sends a value back to the caller; without it, a function returns `None`
* Variables created inside a function are **local** to that function

Functions are one of the most important tools for writing **organized, reusable, and readable** Python programs.
