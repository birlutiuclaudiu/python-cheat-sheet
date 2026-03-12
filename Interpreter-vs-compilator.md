# Compiler vs Interpreter

This document explains the **difference between a compiler and an interpreter**, including definitions, characteristics, and examples.

---

# 1. What is a Compiler?

## Definition

A **compiler** is a program that **translates the entire source code of a program into machine code before the program runs**.

The output is usually an **executable file** that can be run directly by the computer.

---

## How a Compiler Works

Steps:

1. The programmer writes the **source code**.
2. The compiler reads the **entire program**.
3. It translates the code into **machine code**.
4. If there are no errors, an **executable program** is produced.

---

## Example of Compiled Languages

Examples of languages that use compilers:

* C
* C++
* Rust
* Go

Example C program:

```c
#include <stdio.h>

int main() {
    printf("Hello World");
    return 0;
}
```

The compiler converts this program into a **machine code executable file**.

---

## Characteristics of Compilers

* Translate the **whole program at once**
* Generate an **executable file**
* **Faster execution** after compilation
* Errors are shown **after compilation**

---

# 2. What is an Interpreter?

## Definition

An **interpreter** is a program that **executes code line by line**, translating it during execution.

The program does **not produce a separate executable file**.

---

## How an Interpreter Works

Steps:

1. The programmer writes the **source code**.
2. The interpreter reads **one line at a time**.
3. It translates and executes the line immediately.

---

## Example of Interpreted Languages

Examples of interpreted languages:

* Python
* JavaScript
* Ruby
* PHP

Example Python program:

```python
print("Hello World")
```

The Python interpreter executes the code **directly without compiling the entire program first**.

---

# 3. Key Differences

| Feature           | Compiler               | Interpreter              |
| ----------------- | ---------------------- | ------------------------ |
| Translation       | Entire program at once | Line by line             |
| Output            | Executable file        | No separate executable   |
| Speed             | Faster execution       | Usually slower           |
| Error detection   | After compilation      | Stops at first error     |
| Example languages | C, C++, Go             | Python, JavaScript, Ruby |

---

# 4. Example of Error Handling

## Compiled Language Example

If a C program has errors, the compiler reports them **after checking the entire program**.

Example error:

```c
int x = "hello";
```

The compiler will stop compilation and show an error message.

---

## Interpreted Language Example

Python example:

```python
print("Hello")
print(5 + "text")
print("World")
```

Execution result:

```
Hello
TypeError
```

Explanation:

The interpreter stops when it encounters the error and **does not continue executing the rest of the program**.

---

# 5. Advantages and Disadvantages

## Compiler Advantages

* Faster program execution
* Optimized machine code
* Errors found before execution

## Compiler Disadvantages

* Compilation step takes time
* Harder to test small changes quickly

---

## Interpreter Advantages

* Easier debugging
* Immediate execution
* Good for rapid development

## Interpreter Disadvantages

* Slower execution
* Requires interpreter installed on the system

---

# 6. Example: Python and Compilation

Even though Python is considered **interpreted**, it actually works in two steps:

1. Python code is compiled into **bytecode**.
2. The **Python interpreter** executes the bytecode.

Example:

```
Python code → Bytecode → Python Virtual Machine execution
```

---

# 7. Summary

**Compiler**

* Translates the entire program
* Produces executable files
* Faster execution

**Interpreter**

* Executes code line by line
* No executable file
* Easier debugging

Both methods are important and used in different programming languages depending on the design goals.
