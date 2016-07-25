## mapping models to code
### 4 typed of transformations
<img src="pics/modeltransf.png" width="300">

### ***code smell***
- Any symptom in the source code of a program that possibly indicates a bigger problem
- A heuristic that indicates when to refactor, and what specific technique to use
- Problem in the system model
  - Solution: Model refactoring.
- Code Smell: Problem in the source code
  - Solution: Source code refactoring
  - types of smell:
    - method to long -> extract method
    - duplicated code -> extract methode / extract class / *pull up field**
    - class to large -> extract superclass
    - parameter list too long -> replace parameter with explicit method, introduce parameter object
    - lazy class -> turn the class into an attribute

### Mapping UML class diagrams to Code
- UML classes should be split into Interfaces and implementation classes
- attributes should be non-public instance variables
- signatures of UML operations are mapped straightforward to signatures of Java methods
- inheritance can be mapped
  - inheritance (`extends`)
  - subtyping without inheritance (`implements`)
  - aggregation and delegation

### mapping sequence diagrams to Code
- *opt* block implemented by `if` block

### mapping state diagrams to Code
- a `state` variable is introduced, it respresents the current state
- transitions are modeled in a `switch` statement
  - the switch statement receives the current state
  - in the switch statement the possible next step is chosen via `case:` statements
    - different transitions:
      - epsilon transition (no if)
      - if there is a condition, then us a `if()`
    - *actions* are executed in the case statement
  - if the next *state* is chosen, it is assigned

### mapping contracts to Jave
- check *precondition*:
  - assert the predicate before the beginning of the method, throw an exception if false
- check *postcondition*:
  - Assert the predicate at the end of the method
  - Or throw an exception if the predicate evaluates to false
  - If more than one postcondition is not satisfied, throw an exception only for the first violation
- Check *invariant*:
  - Check invariants at the same time as postconditions
  - Of course this is only an approximation
- Deal with *Inheritance*:
  - Encapsulate the checking code into methods that can be called from subclasses

- `try{...}catch(){...}` syntax for checking pre / postconditions when calling methods that throw exceptions when condition is unfulfilled

#### Heuristics for Implementing Contracts
Be pragmatic, if you don’t have enough time, change your tests in the following order:
1. Omit checking code for postconditions and invariants
  - Often redundant, if you are confident that the code accomplishes the functionality of the method
  - Not likely to detect many bugs unless written by a separate tester
      > Instead of letting java throw a exception "ArrayOutOfBounds", be more friendly and check in a precondition for illegal calls, then you can say "hey you bozo, you called me with an index out of bounds, call me with an index in bounds!" and your code even becomes more stable

2. Omit the checking code for private and protected methods
  - If you are the class implementor or class extender, you can trust these classes more than classes written by others

### Heuristics for Transformations
- For any given transformation, always use the same tool
- keep the contracts in the source code, not in the object design model (eg. with JavaDoc)
  - more likely to be updated when the source code changes
- Use the same names for the same objects
- Have a style guide for transformations

## Code Optimization (to achieve Performance)
- performance is the most important non-functional requirement

### Premature optimization
- After creating a performance-aware design, forget all about efficiency until testing is completed
- During *implementation*, focus on *clarity* and *correctness*, not on *performance*
### design for performance
- a simple design is likely to be both, correct and fast
- **avoid** inherently **expensive operation** whenever possible
  - system calls
  - synchronization
  - network message exchanges
  - disk access (use buffered I/O)
  - memory allocation and copying

### refactoring principles
- why refactor?
  - to improve the design of software
  - to make model and source code easier to understand
- when should we refactor?
  - when you add functionality
  - when you need to fix a bug
  - as you do code reviews
  - when the code starts to smell
- what about performance?
  - worry about performance only, when you have identified the performance problem
