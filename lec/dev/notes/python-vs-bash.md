---
title: "lec/dev/"
subtitle: "python vs bash"
author: "yxm"
---

I started my dev journey automating daily tasks in Bash. I then moved to Python and the difference between
them, in term of both structure and syntax, was shocking to me. At least from my point of view (of someone
coming from Mathematics), Python show me to have a much more clear syntax, allowing a good programming in the
functional paradigm (and in the object-oriented paradigm, as well).

Structure
------------

### compilation

* `Python` is a compiled/interpreted language;
* `Bash` is a scripting interpreted language.

This tell us much about the intention of both languages. Being both compiled and interpreted, Python intends
to have a broad scope. On the other hand, being a scripting language, Bash is focused on automation of tasks
and on maintaining the kernel of a specific operating system (see below). 

### compatibility

* `Python` compiler/interpreter is independent of an operating system.
* `Bash` is the shell for some operating system.

The shell of an operating system is constrained by the processor that will execute its commands. But some
operating systems have demands of specific kinds of processors. This means that:

1. a `Bash` application can be developed only in operating systems that admit `Bash` as a shell;
2. a `Bash` application developed in an operating system X may not be perfectly interpreted in other operating
   system Y, both having `Bash` as a shell.
   
Thus, `Bash` applications are not only dependent of certain operating systems, but actually on that operating
system in which the application was developed. This is a totally different situation when compared with
`Python`.
    

###  modularity

* by construction Python admits modular programming and module repositories as `python-pip`
* there is no canonical way to follow a modular programming with Bash nor there is an official module
  repository
  
This reveals the collaborative aspect of `Python`, while `Bash` is more focused on local work.

### paradigms

In the following we will adopt the following definition:
* we say that a language `L` *admits* a programming paradigm `P` if:
    * `L` comes with builtin functionalities of `P`
    * or `L` is modular and has an official extension that add functionalities of `P`.
    
Furthermore, we note that from a paradigm `P` one can build in `L` aspects of other paradigm `P'`. Keeping
this, we will also adopt that

* a language `L` *models* a programming paradigm `P` if:
    * `L` admits another paradigm `P'` and aspects os `P` comes built as builtin from `P'`;
    * or `L` is modular and has some official extension that build this functionalities of `P` from `P'`.

About this one can say that:

* `Python` is structured in terms of classes, instances (i.e., objects) and methods. Furthermore, new classes,
  instances and methods can be constructed. Thus, `Python` *admits* Object Oriented Programming (OOP).
* `Python` comes with some builtin constructions that mimetize aspects of Functional Programming (FP), as
  composition of functions, higher order functions and some lambda calculus. On the other hand, in `Python`
  functions are not treated as first order entities, so that `Python` *does not* admits FP, but *models* FP.
  
* `Bash` is essentially procedural, hence it does not admits OOP. It is possible to build methods in `Bash`,
  but there is no predefined builtin class of them. Furthermore, it is not modular. Thus, from the
  definitions above, `Bash` *does not* models OOP.
  in `Bash` functions are not first order entities, so that it *does not* admits FP. On the other hand, some
  aspects of FP are builtin, as composition of functions (pipelines). Thus, in some level, `Bash` *models* FP.
  
One should not that there are some non official modules that try to extend FP functionalities in `Bash`. For
example, see [here](https://github.com/ssledz/bash-fun).    

Syntax
--------

### functions

* in Python a function `f()` is evaluated (called) as expected, i.e., putting the variables inside the
  parenthesis:  `f(x,y,...)`
* in Bash a function `f()` is evaluated (called) in a different notation: `f $x $y ...`

### arguments

* in Python the number of arguments of a function is defined explicitly, i.e., it appear explicitly in the
  syntax.
  
```python
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
        
```bash
    function f(){
        statement
        ...
    }
```

### code blocks

* in Python code blocks follow a standard configuration: are controlled by indentation and the header always
  ends with a double point `:`. Indeed:
  
```python
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

```bash
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

### intervals

* in Python integer intervals can be easily defined in a standard way with the built-in function `range()`.
  Furthermore, it can be directly used as a condition inside a `for` loop, providing a simple syntax:
  
```python
    for x in range(i,j):
        sentence
        ...
        sentence
```

* in Bash we have the command/function `seq` that can be used outside a `for` loop. Inside a `for` one can
  also use `seq`, but in the form `$(seq i j)`. There  are other alternatives, as `{i..j}` and `(( k=i; k<=j; k++ ))`.

### Boolean operations

* in Python the Boolean operations are more human readable, being given by English words: `and`, `or`, `not`
* in Bash the Boolean operations are given by symbols: `&&`, `||`, `!`

