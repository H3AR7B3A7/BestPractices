# Clean Architecture

## What is Design & Architecture

**Architecture == Design**

_The goal of software architecture is to minimize the human resources required to build and maintain the required
system._

When architecture is disregarded, producing features becomes harder, development costs increase and productivity grinds to a halt.

_Sow and steady wins the race._

## A Tale of Two Values

**Value = Behavior x Structure**

To management the behavior seems most important, but the greater value is structure when examining the extremes.

_There are two kinds of problems, the urgent and the important. The urgent are not important, and the important are never urgent._

Developers and even more so architects as part of the stakeholders need to fight / struggle for clean architecture.

## Programming Paradigms

- 1938: Alan Turing is writing loops, branches, assignments, subroutines, stacks, ... in binary.
- 1940: Assembler languages, to translate into binary.
- 1951: Grace Hopper invented A0, the first compiler.
- 1953: Fortran
- COBOL, PL/1, SNOBOL, C, Pascal, C++, Java, ...
- 3 Paradigms, telling which 'programming structures' to use:
  - Structured
  - Object-oriented
  - Functional

_Each paradigm **removes** capabilities:_
- goto statements
- function pointers
- assignment

_All of these discoveries were made between 1958 - 1968. No new paradigms since._

means:
- polymorphism to cross architectural boundaries
- functional programming to impose discipline on the location of and access to data
- structured programming as algorithmic foundation of modules

map to goals
- function
- separation of components
- data management

## Structured Programming

Minimum set of structures:
- Selection
- Iteration
- Sequence

_These can both create any program and are provable._

- Provable
  - Euclidean mathematical proof -> prove true
  - Scientific proof -> prove false
- Unprovable

_Structured Programming promotes **functional decomposition** into small falsifiable units._

### Conclusion

_All of the above just helps to impose discipline on **direct transfer of control**._


## OOP

Some definitions:
- "The combination of data and functions" -> unsatisfying
- "A way to model the real world" -> evasive
- "Encapsulation, inheritance and polymorphism" -> ?

### Encapsulation

C had perfect encapsulation through forward declaring in header files.

- C++ broke this perfect encapsulation:

  Class member values need to be declared in header file of that class.
  This was partially repaired by access modifiers (private/ public / protected)

- Java / C# no longer have header files

### Inheritance

_Redeclaration of variables was already possible in C through single inheritance, using some trickery with pure supersets._

In OO we gained:
- Multiple inheritance
- Implicit upcasting

### Polymorphism

_In C STDIN & STDOUT can have different implementations. Applications of pointers to functions existed way before OO._

In OO we gained:
- More safety (No more calling functions through pointers)
- Convenience

### Dependency Inversion

_Inverting source code dependencies through inserting an interface between them, in opposite direction to the flow of control._

Example: Make DB and UI depend on business rules, not mentioning UI or DB in it

Gains:
- Independent deploy-ability
- Independent develop-ability

### Conclusion

_Ability through polymorphism to gain absolute control over every source code dependency, allows for a plugin architecture._

_All of the above just helps to impose discipline **on indirect transfer of control**._

## Functional Programming

_Pure functional languages do not allow for mutated variables._

### Immutability

No concurrency issues
- Race conditions
- Deadlock conditions
- Concurrent update conditions

#### Tradeoffs

- Segregation of mutability:

  Immutable components -> mutable component -> transactional memory

  Transactional memory to protect the mutable variables from concurrency issues,
  using transaction- / retry based schemes.

  Moving processing in immutable components / out of the mutable components.

- Event sourcing

  Only create and read:
  - storing ALL transactions
  - Never updating state
  - Process the data only when needed

### Conclusion

_All of the above just helps to impose discipline on **variable assignment**._

## Design Principles

### SOLID

The goal is, mid-level software structures that:
- Tolerate change
- Are easy to understand
- Are the basis of components that can be used in many software systems

The principles:
- Single Responsibility Principle

  The module has only one reason to change

- Open Closed Principle

  Allow for change in behaviour by adding code, without needing to change it

- Liskov Substitution Principles

  Interchangeable parts must adhere to a contract that allows substitution

- Interface Segmentation Principles

  Avoid depending on things we do not use

- Dependency Inversion Principle

  High level policy should not depend on low level details, details should depend on policy

For more details:
[Agile Software Development, Principles, Patterns & Practices - R.C. Martin](https://www.amazon.com/Software-Development-Principles-Patterns-Practices/dp/0135974445)

