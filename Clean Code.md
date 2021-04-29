# Clean Code

## Meaningful Names

*Good*:
- Intentionally revealing
- Meaningful and distinct
- Pronounceable
- Searchable
- Consistent
- Understandable: Computer Science / Domain
- In a meaningful context

*Bad*:
- Disinformation or false clues
- Encoding
- Need for mental mapping
- Being cute
- Puns
- Gratuitous context

**Classes**: nouns or noun phrase  
**Methods**: verbs or verb phrase

## Functions

They should:
- Be small
- Have minimal nesting
- Do one thing / List things at just one level of abstraction
    - Change state of object
    - Return information on an object
- Have structure if they are larger than desired
	- Sections: declarations / initializations / sieve

**Switch Statements** should:
- Appear only once (in an abstract factory)
- Create polymorphic objects
- Be hidden behind an inheritance relationship

**Arguments**:
- Minimal number of arguments (Never more than three)
- They need a good reason to exist
	- A question about the argument
	- Operations on an argument (Move function to argument object?)
	- An event as argument
- Avoid output arguments (Outputs should be in return statement)
    - House the function in the object with the state change
- Avoid flags (booleans)
- Avoid side effects

**Exceptions over Error Codes**

*Error codes*:
- Lead to deeply nested structures
- Caller has to deal with it immediately
- Need for rebuilding when adding new error code

*Exceptions*:
- Separate happy path from error processing
- No need to rebuild: all derivative of exception.class

**Try/Catch** blocks
- Extract the bodies into functions

## DRY

*Don't Repeat Yourself.*

A lot of evolution in languages and frameworks aims avoid repeating code:
- Codd's forms
- OOP
- Aspect oriented programming
- Component oriented programming
- ...

**Structural Programming Rules**:
What Dijkstra said about code block or function:
- One entry
- One exit
- No:
    - break
    - continue
    - goto !!!

**Now**:
These rules are less important now we are able to use smaller functions.
Breaks and continues can help in our expressions.

**Method**:
We start by writing a first draft and then improve our code to apply these good practices.

## Comments

*At best, comments are a necessary evil.*

**GOOD Comments**:
- Legal comments (copyright, ...)
- Informative (Example format, return type ... What?)
- Explanation of intent (Why?)
- Clarification (Readability)
- Warnings of consequence
- TODO
- Amplify (Draw attention)
- Javadocs for public API

**BAD Comments**:
- Mumbling
- Redundant
- Mandated
- Journal
- Noise
- Scary noise
- Position markers
- Closing braces
- Attributions and bylines
- Commented out code
- HTML comments
- Non-logical info
- Too much info
- Inobvious connection
- Function headers
- ...

## Formatting

Formatting tools:  
Consistently apply rules to help communicate the code

*While functionality changes, readability usually continues to affect the maintainability.*

- **Vertical**
    - File / Class size
        - Smaller = More easy to read
    - Blank lines are viual cues
    - Vertical density should indicate relations
    
Locations
- Local variables at the top of functions
- Control values for loops in loop statements
- Instance variables at top of class
- Dependant functions should be vertically close
    - Caller should be above the callee
- Functions with conceptual affinity should be vertically close

- **Horizontal**
    - Keep lines short
    - Closely related values should be horizontally close (like parameters in a function)
    - A space can indicate 'less relation' compared to no space (like with an assignment)
    - We can make precedence of operations more visual with spaces (doesn't work with formatting tool)

*When you feel like a long list of declarations needs spacing in Java, you should probably split the class.*

**Indentation**:  
Visualises the scope hierarchy.
- Avoid breaking the rule on indentation even in compact structures
- Mind dummy scopes (the semicolon after a one liner is easy to miss)

***Teams should agree on a single style of formatting. Consistent gestures help readability a lot.***

## Objects & Datastructutres

Hiding implementation ≠ Layer of functions between the variables.

**Objects**

- Abstractions
- Exposing functions
    - Manipulating the essence of the object
    - Not knowing the implementation

**Data structures**
- Exposing data
- No meaningful functions

**Procedural vs Visitor- or Dual-Dispatch Pattern**
Sometimes you really do want simple data structures with procedures operating on them.
(It is just a myth that "everything is an object".)

### The Law of Demeter

*(Modules shouldn't know about innards of the objects it manipulates.)*

A method **f** of a class **C** should only call methods of these:
- C
- An object created by f
- An object held in an instance variable of C

The method should NOT invoke methods on objects that are returned by any of the allowed functions.
("Talk to friends, not to strangers.")

**Chained calls are generally sloppy programming and often rightfully called train wrecks.**

These are in violation of Demeter only if the methods call for objects, but not when just accessing data structures. The difference often gets obscured by accessor functions.

If they are objects we should ask ourselves what we need them for. We should make the initial object 'DO' something for us.
This way we avoid having to know about the inners of the objects.

### Data Transfer Objects

Uses:
- Communication with databases
- Parsing from sockets
- ...

**Beans** are almost equivalent to this, but with accessor functions are 'quasi-encapsulated' without any real benefit.

**Active records** are a special form of DTO, with navigational methods like *save* and *find*.

None of these data structures should contain any business logic, which belongs in separate objects.

## Error Handling

*Error handling is important, but if it obscures logic, it's wrong.*

It is cleaner to throw an exception in the callee than it is to use return codes in the caller.

Starting with a Try-Catch-Finally statement will help us define a scope to which we can safely add logic using TDD.

Checked exceptions violate the Open-Closed principle. A change in low level code can force many higher classes add exceptions to method signatures.
This is why other languages don't have any, and we should use unchecked exceptions. They are only useful in critical libraries, not when writing applications.

An exception should provide adequate context in a good error message to locate the error.

### Defining Exceptions

Classifications:
- Source
- Type

How to catch them:
- We should think about a 'common exception type' when we need to catch multiple exceptions.
- Often a wrapper can help us catch and translate exceptions (of a 3d party API).
  - Minimize dependencies
  - Easy to swap out libraries later
  - Easy to mock out 3d party calls in testing
  - Not tied to 3d party API design

One exception class is sufficient for an area of code, unless we want to catch one exception and allow another to pass through.

### Defining Normal Flow

Even better than handling an exception is making it part of the normal flow, by using something like the *Special Case Pattern*.
The client code doesn't need to handle the exception if it is encapsulated in a special case object.

### Don't Return Null

Passing null to a method is even worse than returning null.

Fixes:
- Exception + handling
- Assertions

We'd still have a runtime error, and it is better to forbid passing null in the first place!

## Boundaries

We should keep clean boundaries between our software and foreign code.

Conflicting interests:
- Provider: broad applicability
- User: focus on needs

By wrapping we can make the code easier to read and harder to misuse. We can enforce design and business rules upon this wrapper.

**Learning tests** can help us understand third party code.
We shouldn't thoroughly test the third party API, but small tests similar to how we use that API can help differentiate problems 
in our own code from misunderstandings about the foreign code.

We can handle yet unwritten code the same way. By temporarily creating the API we wish we had we can write concise code for it.
We can then write a wrapper for the actual code when eventually the code is developed.

## Unit Tests

*If we let our tests rot, the production code will rot too.*

Three laws of TDD:
- You may not write production code until you have written a failing test.
- You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
- You may not write more production code than is sufficient to pass the current failing test.

*This way of working will generate A LOT of tests, which we need to manage and keep clean.*

Our tests are just as important as production code. A mess in the testing suite will lead to loss of maintainability and eventually abandonment.
Losing our tests is losing confidence to make changes to our code, not knowing if we introduced bugs when doing so.

**Readability** is even more key in unit tests than in production code.
- Avoid code repetition
- Refactor out irrelevant details (Creating a 'Testing API')
- Make 'BUILD-OPERATE-CHECK' structure visible
- Prefer readability to efficiency (memory/CPU)
- Keep tests small and clear
- One assert per test (as a guideline)
  - Test a single concept

FIRST (Object Mentor Training Materials idea of writing clean tests)
- Fast: They should run quickly
- Independent: They should not depend on each other
- Repeatable: They should be repeatable in any environment
- Self-Validating: They should either pass or fail (no investigating)
- Timely: They should be written right before production code

## Classes

Order:
- public static finals (constants)
- private static variables
- private instance variables
- public functions
  - private functions called by them right after

We look for ways to maintain privacy (encapsulation), but will allow protected / package private variables or utility functions to be accessible by a test.

Rules a clean class adheres to:
- Small size (No 'god' classes)
  - Single responsibility
    - A description shouldn't require 'and/if/or' (concise name/description)
    - If something prevents the class to be reusable, it probably doesn't belong
  - Small number of instance variables
    - Each method should operate on one or more of them (cohesion)
    - Instance variables serving to keep a subset of methods small almost always means they belong in a new class
    - Refactoring methods while keeping parameter lists small will generate more instance variables and thus possible new classes
- Open-Closed Principle
  - We use interfaces and abstract classes to isolate concrete details from changes in the code

## Systems

Abstractions and modularity are key for components to work effectively.

### Separating construction from use:

**Separation of main:**
- Main:
  - Consistent strategy for resolving major dependencies
- Application
  - Use interfaces that call on these dependencies

**Dependency Injection:**

*(The application of Inversion of Control to dependency management)*

An authoritative mechanism, either a main routine or a special-purpose container, is responsible for resolving dependencies.

The Spring framework provides the best known DI container for Java.

### Scaling up:

*The architecture of software systems can grow incrementally **IF** proper separation of concerns is maintained.*






---
*Work in progress...*