# Python Recursive Functions — Definition and Examples

This document explains **recursive functions** in Python in a simple way, with many examples so students can see exactly how they work.

---

# 1. What Is a Recursive Function?

A **recursive function** is a function that **calls itself**.

It is used to solve a problem by breaking it into a **smaller version of the same problem**, until the problem becomes so small it can be answered directly.

Every recursive function needs two parts:

* **Base case** — the simple case that stops the recursion (no more calls)
* **Recursive case** — the function calls itself with a smaller/simpler input

```python
def function_name(parameters):
    if base_case_condition:
        return simple_answer      # stops the recursion
    else:
        return function_name(smaller_input)   # calls itself
```

If a function has **no base case**, it will call itself forever and crash with an error (`RecursionError`).

---

# 2. A First, Very Simple Example

```python
def count_down(n):
    if n == 0:              # base case
        print("Done!")
    else:
        print(n)
        count_down(n - 1)   # recursive case

count_down(5)
```

Output:

```
5
4
3
2
1
Done!
```

Explanation:

* Each call prints `n`, then calls itself with `n - 1`.
* When `n` reaches `0`, the base case stops the recursion.

---

# 3. Example — Counting Up

```python
def count_up(n, max_value):
    if n > max_value:        # base case
        return
    print(n)
    count_up(n + 1, max_value)   # recursive case

count_up(1, 5)
```

Output:

```
1
2
3
4
5
```

Explanation:

The function keeps calling itself with a bigger number, until `n` passes `max_value`.

---

# 4. Example — Factorial

The factorial of `n` (written `n!`) is `n * (n-1) * (n-2) * ... * 1`.

```python
def factorial(n):
    if n == 0:                     # base case
        return 1
    else:
        return n * factorial(n - 1)   # recursive case

print(factorial(5))
```

Output:

```
120
```

Explanation:

* `factorial(5)` = `5 * factorial(4)`
* `factorial(4)` = `4 * factorial(3)`
* `factorial(3)` = `3 * factorial(2)`
* `factorial(2)` = `2 * factorial(1)`
* `factorial(1)` = `1 * factorial(0)`
* `factorial(0)` = `1` ← base case, stops here

Then the results are multiplied back together: `1 * 1 * 2 * 3 * 4 * 5 = 120`.

---

# 5. Example — Sum of Numbers from 1 to n

```python
def sum_to_n(n):
    if n == 0:                 # base case
        return 0
    else:
        return n + sum_to_n(n - 1)   # recursive case

print(sum_to_n(5))
```

Output:

```
15
```

Explanation:

`sum_to_n(5)` = `5 + sum_to_n(4)` = `5 + 4 + sum_to_n(3)` = ... = `5 + 4 + 3 + 2 + 1 + 0 = 15`.

---

# 6. Example — Sum of a List

```python
def sum_list(numbers):
    if len(numbers) == 0:              # base case
        return 0
    else:
        return numbers[0] + sum_list(numbers[1:])   # recursive case

print(sum_list([1, 2, 3, 4]))
```

Output:

```
10
```

Explanation:

Each call takes the first number and adds it to the sum of the **rest of the list**, until the list is empty.

---

# 7. Example — Power (Exponent)

```python
def power(base, exponent):
    if exponent == 0:                     # base case
        return 1
    else:
        return base * power(base, exponent - 1)   # recursive case

print(power(2, 4))
```

Output:

```
16
```

Explanation:

`power(2, 4)` = `2 * power(2, 3)` = `2 * 2 * power(2, 2)` = ... = `2 * 2 * 2 * 2 = 16`.

---

# 8. Example — Fibonacci Sequence

Each number is the sum of the two numbers before it: `0, 1, 1, 2, 3, 5, 8, ...`

```python
def fibonacci(n):
    if n == 0:                    # base case
        return 0
    elif n == 1:                  # base case
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)   # recursive case

for i in range(7):
    print(fibonacci(i))
```

Output:

```
0
1
1
2
3
5
8
```

Explanation:

This function has **two base cases** (`n == 0` and `n == 1`) and calls itself **twice** to add the two previous values.

---

# 9. Example — Sum of Digits

```python
def sum_of_digits(n):
    if n < 10:                              # base case
        return n
    else:
        return n % 10 + sum_of_digits(n // 10)   # recursive case

print(sum_of_digits(1234))
```

Output:

```
10
```

Explanation:

`n % 10` gets the last digit, and `n // 10` removes it, so the function processes one digit at a time.

---

# 10. Example — Reversing a String

```python
def reverse_string(text):
    if len(text) == 0:                        # base case
        return text
    else:
        return reverse_string(text[1:]) + text[0]   # recursive case

print(reverse_string("hello"))
```

Output:

```
olleh
```

Explanation:

Each call moves the first character to the end, after reversing the rest of the string.

---

# 11. What Happens Without a Base Case?

```python
def broken(n):
    print(n)
    return broken(n + 1)   # no base case!

broken(1)
```

Output:

```
1
2
3
...
RecursionError: maximum recursion depth exceeded
```

Explanation:

Without a base case, the function never stops calling itself, and Python eventually raises an error.

---

# 12. Recursion vs. Loops

The same task can often be written with a loop **or** with recursion.

```python
# Using a loop
def factorial_loop(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

# Using recursion
def factorial_recursive(n):
    if n == 0:
        return 1
    return n * factorial_recursive(n - 1)

print(factorial_loop(5))
print(factorial_recursive(5))
```

Output:

```
120
120
```

Explanation:

Both give the same result. Loops are usually simpler and faster; recursion is often clearer for problems that are naturally defined in terms of **smaller versions of themselves** (like factorial, Fibonacci, or working with nested structures).

---

# 13. Summary

* A **recursive function** is a function that calls itself.
* It must have a **base case** (stops the recursion) and a **recursive case** (calls itself with a smaller input).
* Without a base case, the function will run forever and crash with `RecursionError`.
* Common recursion examples: factorial, sum of numbers, Fibonacci, sum of digits, reversing a string.
* Any recursive function can also be rewritten using a loop.

Recursion is a powerful tool once you get comfortable identifying the **base case** and the **smaller step** that moves toward it.
