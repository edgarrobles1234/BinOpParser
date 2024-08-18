# Binary Operator Simplifier 

The goal of this assignment is to get you used creating testing/regression
suites for your program and to write some recursive python code, thinking
about and manipulate data representations. 

There are two parts to this assignment. The first involves creating a
testing/regression framework. The second involves creating a simplifier to
reduce various mathematical identities in an AST. You will be required to
implement reduces for the arithmetic identity and multiplicative identity.
There are also optional implementations multiplication by zero and constant
folding if you would like additional practice. 

Our language for (most of) this assignment will be a simple arithmetic
language that consists of numbers, addition, and multiplication.

## Part 1 - Testing Framework

For the first part of the assignment, you will implement a simple testing
framework. While their are lots of ways do accomplish this, we will use a
file based testing setup for this assignment. Thus, your directory should
contain a top level folder called `testbench` with two subdirectories for
testing whichever pieces you've implemented plus one more for the combined
tests. Each of those will have directories called `inputs` and `outputs` to
hold their tests.  So for a test called `simple` in each test, your
directory structure would look like this:

```
.
├── README.md
├── binexp_parser.py
└── testbench
    ├── arith_id
    │   ├── inputs
    │   │   └── simple
    │   └── outputs
    │       └── simple
    ├── combined
    │   ├── inputs
    │   │   └── simple
    │   └── outputs
    │       └── simple
    ├── constant_fold
    │   ├── inputs
    │   │   └── simple
    │   └── outputs
    │       └── simple
    ├── mult_by_zero
    │   ├── inputs
    │   │   └── simple
    │   └── outputs
    │       └── simple
    └── mult_id
        ├── inputs
        │   └── simple
        └── outputs
            └── simple
```
Your program should be setup so that adding a new test only involves adding
the input file and the three output files. In addition to testing, this will
give you additional familiarity with walking directory structures.


## Part 2 - Implementing your Reducer 

Your task is to take as input a prefix equation, parse it into an AST, and
then perform various reductions on it. There are two required
transformations and two optional transformations given as an option for
extra practice, or if you find this kind of thing fun.

You are provided with an example implementation for the parser, AST builder,
and printer that was done fairly quickly, so it's not perfect! You may feel
free to build off of it, or take it as inspiration and write something
better.

### Task 1: Arithmetic Identity

The first reducer is to eliminate any additions by 0, aka the arithmetic
identity.

So an input of `+ 1 + 2 0` would simply reduce to `+ 1 2`.

### Task 2: Multiplicative Identity

The second reducer is to eliminate any multiplications by 1, aka the
multiplicative identity.

So an input of `+ 1 * 2 1` would simply reduce to `+ 1 2`.

### Optional Task 3: Multiply by Zero

The first optional task is to reduce any multiplication by 0 with simply 0.
This one is pretty easy!

An input of `+ 1 * 0 1` would simply reduce to `+ 1 0`

### Optional Task 4: Constant Folding

The final optional task is to implement constant folding. Constant folding is
taking a static expression of constants and combining them. We can reduce an
expression like `+ 1 * 0 1` to simply `1`. Things get more interesting if we
add in identifiers however! We can't reduce an expression such as `+ 1 x`. If
you choose to implement this stretch feature, you'll basically implement a
simple calculator. It's a bit more interesting if you also add identifiers,
i.e. any string that isn't a number or `+` or `*`, so that your output is more
than just a single number!

## Putting it all together!

You should also include a top level function `simplify_binops` that calls
each of the transformations that you've implemented. Note that something
interesting happens here depending upon the order that you call them. For
example, an expression such as `+ 1 * 0 1` would reduce to 1 if we simplify
the multiplicative identity first then the additive identity. However, if we
did the additive identity reduction then the multiplicative identity
reduction, we would get `+ 1 0`! This is an issue in compilers known as the
``phase ordering problem'' and it's super interesting, but way beyond what
we want to accomplish in this class. I just wanted to point it out to you as
something weird. We'll basically just ignore it for now, pick an order and
call that good enough. 


# Acknowledgements

Thank you to Dr. Aaron Keen and Dr. Ayaan Kazerouni for their help in
brainstorming this assignment!
