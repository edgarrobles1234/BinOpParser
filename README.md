# Binary Operator Parse and Printer

The goal of this assignment is to get you used creating testing/regression
suites for your program and to write some recursive python code, thinking about
data representations.

There are two parts to this assignment. 

## Part 1 - Testing Framework

For the first part of the assignment, you will implement a simple testing
framework. While their are lots of ways do accomplish this, we will use a file
based testing setup for this assignment. Thus, your directory should contain a
top level folder called `testbench` with two subdirectories, `inputs` and
`outputs`. The `outputs` directory should contain three subdirectories for
outputs of all three forms, `infix`, `prefix`, and `postfix`. 


So for a test called `simple`, your directory structure would look like this:
.
├── README.md
├── binexp_parser.py
└── testbench
    ├── inputs
    │   └── simple
    └── outputs
        ├── infix
        │   └── simple
        ├── postfix
        │   └── simple
        └── prefix
            └── simple

Your program should be setup so that adding a new test only involves adding the
input file and the three output files. In addition to testing, this will give
you additional familarity with walking directory structures.


## Part 2 - Implementing your Program

You should implement a simple parser that reads in a string that
represents a simple mathematical equation in prefix notation. Your program
should parse that string into an abstract syntax tree. Once that works, you'll
then need to be able to print out equation in either prefix, postfix, or infix
notation. Note that producing fully parenthesised expressions for infix
notation is fine.

This project contains an example implementation that was done fairly quickly,
so it's not perfect! You may feel free to build off of it, or take it as
inspiration and write something better.
