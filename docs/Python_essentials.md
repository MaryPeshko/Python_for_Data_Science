# Python\_essentials

# Interpreted Runtime vs. Compiled Executables

Why C/C++ Doesn't Use Virtual Environments in the Same Way

Python is an interpreted language. When you run `python script.py`, the interpreter searches shared path directories (like `site-packages`) at runtime to import packages.

C and C++ compile source code directly into machine-code binary executables. During compilation, the compiler and linker resolve header files and static (`.a` / `.lib`) or dynamic (`.so` / `.dll`) libraries explicitly specified via build scripts (like CMake or Makefiles).

In C/C++, dependencies are linked directly into the binary or managed in project-specific build directories rather than being installed into a single shared global interpreter folder.

# Library and dependency

While the terms **library** and **dependency** are often used interchangeably in casual discussion, they do not mean the exact same thing in either Python or C/C++.

A **library** is a piece of code (a collection of modules or binaries), while a **dependency** describes a relationship — anything your program *depends* on to compile or run.

## 1\. In the Context of Python (Runtime)

* **Library:** Reusable code packages that you import and call directly in your code (for example, `fastapi` or `uvicorn`).  
* **Dependency:** The full set of components required for your code or environment to work at runtime:  
  * **Direct vs. Transitive Dependencies:** When you install a library like FastAPI, it relies on other underlying sub-libraries to function. Commands like `pip freeze` inspect your `.venv` directory, identify FastAPI along with all of its secondary dependencies, and write them to a requirements.txt file.  
  * **System & Runtime Dependencies:** Python itself (such as Python 3.12) and environment tools like `pip` are runtime dependencies for your application.

At runtime, Python’s interpreter searches `site-packages` inside your virtual environment to resolve these libraries dynamically when an `import` statement is executed.

## 2\. In the Context of C/C++ (Compilation & Build)

* **Library**: The specific compiled artifact or header collection—such as header files (`.h/.hpp`) and compiled library archives (`.a/.lib` for static linking, or `.so/.dll` for dynamic linking).  
* **Dependency**: Everything needed to build or execute the binary:  
  * **Build-time / Compile-time Dependencies:** The compiler toolchain (e.g., `gcc` or `clang`), build automation systems (`make` or `cmake`), header files, and static libraries needed during linking.  
  * **Runtime Dependencies:** If a C/C++ library is **statically linked** (.a), the library code is copied directly into the executable binary, meaning the library is no longer a runtime dependency. If it is **dynamically linked** (`.so/.dll`), the operating system's loader must locate those shared libraries on the host system when the application launches.

### Summary

**Aspect: Definition**

**Library:** A specific collection of reusable functions, classes, or modules.

**Dependency:** Any component (library, interpreter, etc.) required to build or run software.

&nbsp;

**Aspect: Python Context**

**Library:** Packages installed and imported in scripts (e.g., import fastapi).

**Dependency:** The full graph of primary libraries, sub-dependencies, and the Python runtime itself.

&nbsp;

**Aspect: C/C++ Context**

**Library:** Header files (`.h`) and binary files (`.a, .so, .lib, .dll`).

**Dependency:** Build tools, compilers, headers, static libraries at compile time, and shared libraries at runtime.

&nbsp;

---

# Dynamic typing

&nbsp;

# Indentation as syntax

&nbsp;

# Control flow&nbsp;

&nbsp;

# Modules&nbsp;

Modules are Python's add-ons.

# Types

## Literals

### Numeric literals

Python does allow, though, the use of **underscores** in numeric literals.

Therefore, you can write this number either like this: `11111111`, or like that: `11_111_111`.

### Type hint

a: int \= 111\_111

&nbsp;

???? Python float representation is approximate?

&nbsp;

There is one more, special literal that is used in Python: the `None` literal. This literal is a so-called `NoneType` object, and it is used to represent the absence of a value.

# Operators

## Basic operators

We'll begin with the operators which are associated with the most widely recognizable arithmetic operations:

`+`, `-`, `*`, `/`, `//`, `%`, `**`

A `**` (double asterisk) sign is an **exponentiation** (power) operator.

A `/` (slash) sign is a **divisional** operator.

The value in front of the slash is a **dividend**, the value behind the slash, a **divisor**.

Python’s `//` is **floor division**.

### Modulo

Division by negative value is specific.

In Python, `%` is **defined using `//`**:

a % b \= a \- (a // b) \* b

##### Example: `2 % -4`

1. Exact division: `2 / -4 = -0.5`  
2. `//` rounds **down** (toward negative infinity): `2 // -4 = -1`  
3. Multiply back: `(-1) * (-4) = 4`  
4. Remainder \= original minus that: `2 - 4 = -2`

&nbsp;

### Operators and their bindings

Most of Python's operators have left-sided binding, which means that the calculation of the expression is conducted from left to right.

```py
print(9 % 6 % 2)
```

&nbsp;

The result clearly shows that **the exponentiation operator uses right-sided binding**.

```py
print(2 ** 2 ** 3)
```

### **replication operator**&nbsp;

The `*` (asterisk) sign, when applied to a string and number (or a number and string, as it remains commutative in this position) becomes a **replication operator**.

For example, `"James" * 3` gives `"JamesJamesJames".`

# **Conditional Execution**

This conditional statement consists of the following, strictly necessary, elements in this and this order only:

* the `if` keyword;  
* one or more white spaces;  
* an expression (a question or an answer) whose value will be interpreted solely in terms of `True` (when its value is non-zero) and `False` (when it is equal to zero);  
* a **colon** followed by a newline;  
* an **indented** instruction or set of instructions (at least one instruction is absolutely required); the **indentation** may be achieved in two ways \- by inserting a particular number of spaces (the recommendation is to use **four spaces of indentation**), or by using the *tab* character; note: if there is more than one instruction in the indented part, the indentation should be the same in all lines; even though it may look the same if you use tabs mixed with spaces, it's important to make all indentations **exactly the same** \- Python 3 **does not allow mixing spaces and tabs** for indentation.

### The elif statement

The second special case introduces another new Python keyword: **elif**. As you probably suspect, it's a shorter form of else if.

# **Loops**

## while loop

In general, in Python, a loop can be represented as follows:&nbsp;

```py
while conditional_expression:
    instruction 
```

&nbsp;

An instruction or set of instructions executed inside the `while` loop is called the **loop's body**;

## for loop

```py
for i in range(100):
    # do_something()
    pass 
```

&nbsp;

* any variable after the *for* keyword is the **control variable** of the loop; it counts the loop's turns, and does it automatically;  
* the *in* keyword introduces a syntax element describing the range of possible values being assigned to the control variable;  
* the `range()` function (this is a very special function) is responsible for generating all the desired values of the control variable; in our example, the function will create (we can even say that it will **feed** the loop with) subsequent values from the following set: 0, 1, 2 .. 97, 98, 99;&nbsp;  
  * **note:** in this case, the `range()` function starts its job from 0 and finishes it one step (one integer number) before the value of its argument;  
* note the *pass* keyword inside the loop body \- it does nothing at all; it's an **empty instruction** \- we put it here because the `for` loop's syntax demands at least one instruction inside the body.

## `range()` function

`range()` invocation may be equipped with two arguments, not just one:&nbsp;

```py
for i in range(2, 8):
    print("The value of i is currently", i) 
```

&nbsp;

The `range()` function may also accept **three arguments.** The third argument is an **increment** \- it's a value added to control the variable at every loop turn (as you may suspect, the **default value of the increment is 1**).&nbsp;

The syntax of `range()` looks as follows: `range(start, stop, step)`&nbsp;

```py
for i in range(2, 8, 3):
    print("The value of i is currently", i)
```

&nbsp;

# **Logical Operations**

## and

`and` is a logical conjunction operator in Python. It's a **binary operator with a priority that is lower than the one expressed by the comparison operators**.&nbsp;

## or

`or` is a disjunction operator. It's a **binary operator with a lower priority than** `and` (just like `+` compared to `*`).

## not

It's a **unary operator performing a logical negation**.&nbsp;

# **Bitwise Operations**

`xor` (as in **exclusive or**) operator, and is denoted as `^` (caret).&nbsp;

Here are all of them:

* `&` (ampersand) \- bitwise conjunction (and);  
* `|` (bar) \- bitwise disjunction (or);  
* `~` (tilde) \- bitwise negation (no);  
* `^` (caret) \- bitwise exclusive or (xor).

&nbsp;

\| Argument `A` \| Argument `B` \| `A & B` \| `A | B` \| `A ^ B` \|&nbsp;

\|          `0`          \|          `0`           \|      `0`     \|      `0`     \|      `0`      \|&nbsp;

\|          `0`          \|          `1`           \|      `0`     \|      `1`     \|      `1`      \|

\|          `1`          \|          `0`           \|      `0`     \|      `1`     \|      `1`      \|

\|          `1`          \|          `1`           \|      `1`     \|      `1`     \|      `0`      \|

&nbsp;

Let's make it easier:

* `&` requires exactly two `1`s to provide `1` as the result;  
* `|` requires at least one `1` to provide `1` as the result;  
* `^` requires exactly one `1` to provide `1` as the result.

&nbsp;Let's assume that the following assignments have been performed:&nbsp;

```py
i = 15
j = 22
bit = i & j 
```

&nbsp;

The `&` operator will operate with each pair of corresponding bits separately, producing the values of the relevant bits of the result. Therefore, the result will be as follows:&nbsp;

| `i` | `00000000000000000000000000001111` |
| :---- | :---- |
| `j` | `00000000000000000000000000010110` |
| `bit = i & j` | `00000000000000000000000000000110` |

&nbsp;

These bits correspond to the integer value of **six**.&nbsp;

## `~` (tilde) \- bitwise negation

Let's look at the **negation operators** now. First the logical one:

```py
i = 15
bitneg = ~i
```

&nbsp;

It may be a bit surprising: the `bitneg` variable value is `-16`. This may seem strange, but it isn't at all. If you wish to learn more, you should check out the binary numeral system and the rules governing two's complement numbers.

| `i` | `00000000000000000000000000001111` |
| :---- | :---- |
| `bitneg = ~i` | `11111111111111111111111111110000` |

&nbsp;

&nbsp;

# **Lists and List Processing**

&nbsp;

&nbsp;

&nbsp;

## Data structures

**What is a Tuple?**

A tuple is an immutable (unchangeable) collection of ordered elements in Python.

List is mutable.

&nbsp;

---

typing — Support for type hints [https\://docs.python.org/3/library/typing.html\#](https://docs.python.org/3/library/typing.html#)

&nbsp;

---

**assert** is a Python statement that checks if something is **True**. If it's False, the program crashes with an error.

Basic Syntax:

`assert condition, "Error message if condition is False"`

&nbsp;

# Generator&nbsp;

&nbsp;

# Built-in functions

To find the largest number you can use a Python built-in function called `max().`&nbsp;

## print()

The way we've used it here is called *multi-line printing*. You can use **triple quotes** to print strings on multiple lines in order to make text easier to read, or create a special text-based design.

```py
print(
"""
+================================+
| Welcome to my game, muggle!    |
| Enter an integer number        |
+================================+
""")

```

&nbsp;

##### Separate letters with a new line

Unpack the string into print, using sep for the separator.

```py
print(*text, sep="\n") 
```

## enumerate()

If you need the index.

```py
text = "Hello"
for i, letter in enumerate(text): 
    print(i, letter) 
```

&nbsp;