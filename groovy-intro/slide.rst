===================
Groovy Introduction
===================

--------------------------------------------
A Dynamic Language based on the JVM platform
--------------------------------------------

:Author: Jerry Peng <pr2jerry@gmail.com>


Powerful Platform, Old Language
===============================
- JVM is a powerful platform
    - Industry-standard
    - Performance
    - Security
    - Stability
    - Existing tools, libraries
- The Java language is really old
    - Lack of important features of modern languages
        - First-class functions, closure, etc.
    - Verbose
    - Slowly evolving
        - Java 7, 8

Alternative Languages on JVM
============================
- Groovy, Jython, JRuby
    - Dynamic language
- Scala
    - Static language
    - Actor model
    - Really complex
- Clojure
    - Lisp dialect with modern features
        - Macros, code as data, pure functional
        - Immutable data structure
    - Software transactional memory

Alternative Languages on JVM
============================
It is worth learning one or more of these languages.

- Think Different
    - OO vs Functional
    - Dynamic vs Static
- Use these languages in Java projects


Introduction to Groovy
======================
- Dynamic language
- First-class function and closure
- Easy to read and learn
    - Compatible with Java syntax
- DSL support

First Sight on Groovy
=====================
Hello world::

    class HelloWorld {
        
        static main(args) {
            println("Hello world");
            println "Hello world"
            def name = "WKS"
            println "Hello to ${name}"
        }
    }

First Signt on Groovy
=====================
- Parentheses are optional if there is only one argument
- Variable type is optional
- Groovy template

Install & Run
=============
- Need a JDK installed (JAVA_HOME, PATH)
- Configure GROOVY_HOME and PATH
- REPL(Read Evaluation Print Loop)
    - Groovy Shell (groovysh)
    - REPL is great for test/experiment/learning
- Run a groovy script::

    groovy xxx.groovy

- Install guide [1]_.

.. [1] http://groovy.codehaus.org/Installing+Groovy


A Brief Tour of Groovy Features
===============================
- Just an introduction
    - Still unfamiliar with Groovy
- Need to explore the language by yourself
    - Use groovy shell to do experiments
- Features to introduce:
    - First class function and closure
    - Regular expression
    - Groovy string template

Functional Programming
======================
- First-class function
    - Function is also a kind of object
    - Could be created on the fly
    - Function could be used as argument or return value
- Anonymous function (function without a name)
    - In Groovy, it is called Block

Functional Programming
======================
Functions could be assigned to variables::

    groovy:000> add = {x, y -> x + y}
    ===> groovysh_evaluate$_run_closure1@1c19919
    groovy:000> add(10, 9)
    ===> 19
    groovy:000> square = {it * it}
    ===> groovysh_evaluate$_run_closure1@a166bd
    groovy:000> square(9)
    ===> 81


Functional Programming
======================
Functions could be passed as aruguments::

    groovy:000> [1, 2, 3, 4, 5].collect {it * 2}
    ===> [2, 4, 6, 8, 10]
    groovy:000> (1..20).findAll {it % 2 == 1}
    ===> [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
    groovy:000> ["OneMS", "SPU", "iSharing"].each {println it}
    OneMS
    SPU
    iSharing
    ===> [OneMS, SPU, iSharing]

- Collection class have methods that take function as arguments
    - find, findAll
    - collect
    - inject


Functional Programming
======================
Map/Reduce, a concept originated from functional programming,
now popular in distributed computing::




- Closure
    - A enclosed function that binds its enclosing scope
    - A means to bind data with function

