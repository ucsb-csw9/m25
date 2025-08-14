---
num: "Lecture 6"
desc: "Recursion, Python Lists vs. Dictionaries, Midterm Guide"
ready: true
lecture_date: 2025-08-14 14:00:00.00-7:00
---

Recorded Lecture: [8_14_25](https://drive.google.com/file/d/14kqGiq4m6sWDSWe3Spea1PCqRVxKtyCU/view?usp=drive_link)

# Recursion

* Recursion is when a function contains a call to itself
* Recursive solutions are useful when the result is dependent on the result of sub-parts of the problem

## The three laws of recursion

1. A recursive algorithm must have a base case
2. A recursive algorithm must change its state and move toward the base case
3. A recursive algorithm must call itself, recursively

In general, recursive solutions must use the solution of subparts of the problem to solve a general problem. 

## Common Example: Factorial

* N! = N * (N-1) * (N-2) * ... * 3 * 2 * 1
* N! = N * (N-1)!
* We can solve N! by solving the (N-1)! sub-part
    * Note: 0! == 1

```
def factorial(n):
    if n == 0:      # base case
        return 1
    return n * factorial(n-1)
```

## Function Calls and the Stack

* The `Stack` data structure has the First in, Last out (FILO) property
* We can only access the elements at the top of the stack
    * Analogy: Canister of tennis balls
        * In order to remove the bottom ball, we have to remove all the balls on top 
* We won't go through an implementation yet, but we can conceptualize this on a high-level
* Function calls utilize a stack ("call stack") and organize how functions are called and how expressions that call functions wait for the functions' return values
    * When a function is called, you can think of that function state being added (or "pushed") on the stack
    * When a function finishes execution, it gets removed (or "popped") from the stack
    * The top of the stack is the function that is currently running
* Example

```
def double(n):
    return 2 * n

def triple(n):
    return n + double(n)

print(triple(5))
```

![triple.png](triple.png)

* Going back to our recursive factorial example, let's trace `factorial(3)`

![factorial.png](factorial.png)

## Common Example: Fibonnaci Sequence

* A fibonacci sequence is the nth number in the sequence is the sum of the previous two (i.e. f(n) = f(n-1) + f(n-2)).
* f(0) = 0, f(1) = 1, f(2) = 1, f(3) = 2, f(4) = 3, f(5) = 5, f(6) = 8, ...

```
def fibonnaci(n):
    if n == 1:    # base cases
        return 1
    if n == 0:          
        return 0

    return fibonnaci(n-1) + fibonnaci(n-2)
```

* Evaluate `fibonnaci(4)` by hand

```
fib(3)                    +  fib(2)
fib(2)          + fib(1)  +  fib(2)
fib(1) + fib(0) + fib(1)  +  fib(2)
1      + fib(0) + fib(1)  +  fib(2)
1      + 0      + fib(1)  +  fib(2)
1      + 0      + 1       +  fib(2)
1      + 0      + 1       +  fib(1) + fib(0)
1      + 0      + 1       +  1      + fib(0)
1      + 0      + 1       +  1      + 0
3
```

# Python Lists vs. Python Dictionaries

* Let's observe the performance between lists and dictionaries with an example.
* The following program counts the number of words in a file using a list and dictionary
    * They do the same thing, but the performance is vastly different...
    * `wordlist.txt` : File containing a collection of words, one per line.
        * <https://ucsb-cs8.github.io/m19-wang/lab/lab07/wordlist.txt>
    * `PeterPan.txt` : You can download classic novels from the Gutenberg Project as a .txt file!
        * <https://www.gutenberg.org/ebooks/16>

```
# Set up our data structures
DICT = {}
infile = open("wordlist.txt", 'r')
for x in infile: # x goes through each line in the file
    DICT[x.strip()] = 0 # Creates an entry in DICT with key x.strip() and value 0
print(len(DICT))
infile.close() # close the file after we’re done with it.

WORDLIST = []
for y in DICT: # put the DICT keys into WORDLIST
    WORDLIST.append(y)
print(len(WORDLIST))

# Algorithm 1 - Lists
from time import time
start = time()
infile = open("PeterPan.txt", 'r')
largeText = infile.read()
infile.close()
counter = 0
words = largeText.split()
for x in words:
    x = x.strip("\"\'()[]{},.?<>:;-").lower()
    if x in WORDLIST:
        counter += 1
end = time()
print(counter)
print("Time elapsed with WORDLIST (in seconds):", end - start)

# Algorithm 2 - Dictionaries
start = time()
infile = open("PeterPan.txt", 'r')
largeText = infile.read()
infile.close()
words = largeText.split()
counter = 0
for x in words:
    x = x.strip("\"\'()[]{},.?<>:;-").lower()
    if x in DICT: # Searching through the DICT
        counter += 1
end = time()
print(counter)
print("Time elapsed with DICT (in seconds):", end - start)
```

* Python lists are efficient if we know the index of the item we're looking for
    * The reason why adding to the front of the list is costly is because lists have to "make room" for the element to be at index 0
        * All existing elements of the list need to shift one index up in order for the inserted element to be placed at index 0
    * Adding to the end of the list is not nearly as costly because no shifting of existing elements needs to occur
* For this example, since we are looking for the value in the list (without knowing the index), we are checking through the entire WORDLIST for every word in `PeterPan.txt`

* Python dictionaries are efficient when looking up a key value
    * Dictionary values are actually stored in an underlying list
    * Keys are converted into a numerical value, which is passed into a **hash function**
        * The purpose of the hash function is to output the index for the underlying list based on the key value
        * We do not have to scan the underlying list structure since a key will always be placed into a specific location in the the underlying list
        * We won't go into the implementation now, but we'll revist this in more detail later
* There are MANY ways to solve a problem in programming, but understanding how certain tools work and making the best decisions is important!

# Midterm High-Level Guide

* Link to previous M23 in-person Midterm: [M23 Sample Midterm](https://drive.google.com/file/d/1BoCF4FLUFXxVj9NhvHFSbLgfPghH38VB/view?usp=drive_link)

    * Note: use this as a **supplemental** study guide - the content, format, and difficulty may vary.

```
Time:
* Gradescope (online assignment), Thursday 8/21 2pm - 3:20pm PST

We will be monitoring Piazza during the midterm exam time.
* For any CLARIFYING quesitons, you may post a PRIVATE question on
Piazza where we will answer them.
* If there needs to be a change / modification in any question, then
we will post any clarifications publicly on Piazza (Piazza will send
an email)

Midterm Topics:

Will cover material from the beginning of the class up until the end of week 2 (today's) lecture, h00 - h03, lab00 - lab03

Python Basics 
- Types
    * I don't expect students to know ALL Python basics, but do expect students to know the ones we explicitly covered in lectures and/or assignments
    * int, float, boolean, strings, lists, sets, dictionaries, ...
    * conversion functions (int(), float(), str(), ...)
    * mutable vs. immutable
- Relational / logical operators (==, <, >, <=, >=, and, or, not, ...)
- Python Lists
    * Supporting methods (count, pop, append, insert, ...)
    * List / string slicing [:]
- Under-the-hood dictionary workings (hash function)
- Strings
    * Supporting methods (replace, split, find, ...)
- Function definitions
- Control Structures (if, else, elif, for, while, ...)

Python Errors / Exceptions
- Runtime vs. Syntax
- Exception types
- Exception handling
    * try / except / raise
    * Flow of execution
    * Passing exceptions to function / method caller(s) when not handled in try / except
    * Multiple except blocks
    * Handling Exceptions in an Inheritance hierarchy

Object Oriented Programming
- Defining classes and methods
- constructors (defining / initializing default state)
- Shallow vs. Deep equality (overloading __eq__ method)
- Overloading operators (__str__, __add__, __le__, ...)
- Inheritance
    * Know method lookup for inheritance hierarchy
    * implementation for inherited fields / methods
    * overriding inherited methods
    * calling super / base class(es) methods

Testing
- Test Driven Development (TDD)
- pytest

Algorithm Analysis and O-notation
- Know how to derive O-notation for snippets of code

Recursion
- Implementation of recursive functions
- Understanding how recursive algorithms are managed by the call stack
- Note: I'll defer deriving O-notation questions for recursive functions / methods to the final exam
```
