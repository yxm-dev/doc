---
title: "lec/dev/"
subtitle: "python vs bash"
author: "yxm"
---

I started my dev journey by automating daily tasks in Bash. I then moved to Python and the difference between
them, in term of structure and syntax, was a shock to me. At least from my point of view (of someone coming
from Mathematics), Python show me to have a much more clear syntax, allowing a good programming in the
functional paradigm (and in the object-oriented paradigm, as well).


General
------------

### 1. compilation

* Python is a compiled/interpreted language.
* Bash is a scripting interpreted language.

### 2. modularity

* by construction Python admits modular programming and module repositories as `python-pip`
* there is no canonical way to follow a modular programming with Bash nor there is an official module
  repository

Syntax
--------

### 3. functions

* in Python a function `f()` is evaluated (called) as expected, i.e., putting the variables inside the
  parenthesis:  `f(x,y,...)`
* in Bash a function `f()` is evaluated (called) in a different notation: `f $x $y ...`

### 4. arguments

* in Python the number of arguments of a function is defined explicitly, i.e., it appear explicitly in the
  syntax.
```
    def f(x,y,...):
        statement
        ...
```
* in Bash the number of arguments of a function is maximal and implicit. This means that:
    * a function can be evaluated in (called with) any number of variables, unless it provides some error.
      This follows from the fact that Bash comes with a predefined empty state which allows it to extend any
      function to any number of variables by adding constant values at the empty state for the not used
      variables.
    * it does not appear explicitly in the syntax:
```
    f(){
        statement
        ...
    }
```

### 5. code blocks

* in Python code blocks follow a standard configuration: are controlled by indentation and the header always
  ends with a double point `:`. Indeed:
```
    def f(x,y,...):
        statement
        ...
        statement
        
    for x in interval:
        statement
        ...
        statement
        
    if condition:
        statement
        ...
    elif condition:
        statement
        ...
    else:
        statement
        
    while condition:
        statement
        ...
        statement
```
* in Bash block codes are controlled by brackets or specific additional beginning/ending keywords.
  Furthermore, indentation plays no role:
```
    function f(){
        statement
    statement
    ...
    }

    for x in interval; do
        statement
    statement
    ...
    done

    if condition; then
        statement
        ...
    elif condition; then
    statement
    ...
    else
        statement
    fi
    
    while condition; do
        statement
    statement
    ...
    done
           
```

### 6. intervals

* in Python integer intervals can be easily defined in a standard way with the built-in function `range()`.
  Furthermore, it can be directly used as a condition inside a `for` loop, providing a simple syntax:
```
    for x in range(i,j):
        sentence
        ...
        sentence
```
* in Bash we have the command/function `seq` that can be used outside a `for` loop. Inside a `for` one can
  also use `seq`, but in the form `$(seq i j)`. There  are other alternatives, as `{i..j}` and `(( k=i; k<=j; k++ ))`.

### 7. Boolean operations

* in Python the Boolean operations are more human readable, being given by English words: `and`, `or`, `not`
* in Bash the Boolean operations are given by symbols: `&&`, `||`, `!`

