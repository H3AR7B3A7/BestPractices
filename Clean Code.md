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

**Objects**

Hiding implementation:
- ≠ Layer of functions between the variables
- = Abstractions
    - Manipulating the essence of the object
    - Not knowing the implementation

**Data structures**

Exposing data w/o meaningful functions


---
*Work in progress...*