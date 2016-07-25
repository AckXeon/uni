## ***OCL (Object constraint language)***
- OCL is part of the UML standard
- OCL is based on predicate calculus
- OCL is used to express constraints, that cannot be modeled in UML
- an ***OCL contract*** is the set of all the invariants, preconditions and postconditions associated with a class diagram
### ***contract***
- an oo contract is an exact specifiaction of the interface of the object. a contract inlucdes three types of predicates
  1. *invariant*: A predicate that is always true for all instances of a class
  2. *precondition*("rights"): A predicate that must be true before an operation is invoked
  3. *postcondition*("obligations"): A predicate that must be true after an operation is invoked
- A contract is called a formal specification, if the invariants, preconditions (“rights” and postconditions (“obligations”) in the contract are unambiguous
- a contract restricts the model space (it constrains, what can be initiated)

### why not use *contracts* during analysis?
Advantage:
  - Constraints can increase the precision of requirements
  - Constraints can yield more questions for the end user
  - Constraints can clarify the relationships among several objects
Trade-offs:
1. Communication among stakeholders
  - A client often does not understand formal constraints
2. Level of detail vs. rate of requirements change
  - It is not worth to precisely specify a concept that will change
3. Level of detail vs. elicitation effort
  - Issue: Is it worth the time interviewing the end user?
  - Will these constraints be discovered during object design anyway?
4. Testing
  - If tests are generated early, do they require the level of precision of a contract?

### ***OCL***:
- *OCL*: a formal language for expressing constraints over a set of objects in a model
- declarative: so side effects, no control flow
- based on sets, multi sets, sequences
- **OCL is a predicate language, declarations only, no "if then else"!**
  - no side effects, not control flow
- OCL expressions evaluate to true of false
  - evaluated either in the context of a class or in the context of an operation
  - constraints apply to all instances

#### OCL expressions and OCL types
- Operands in OCL expressions are objects and properties
- each OCL object has an OCL type, whitch defines the operations that can be called on this object
  - *predefined types*:
    - base types: **Integer, Real, String, Boolean**
    - collection types: **set, bag, sequence**
  - *user defined types*:
    - all the class names in the model<br><br>
- OCL expressions evaluate to *true* or *false*
  - operators on statements: *not, and, or, implies, equals, xor*
- **if two classes are related, but the relation does not have a name, the [targetClassName] is used in lowercases**

- **SYNTAX**:
  ```
  context [Class][]::method] [pre/post] [inv]:
    [EXEC]
    ```
    where:
    - `context` is a keyword
    - `[Class]` specifies the concerned class
    - `[::method]` specifies the concerned method in this context and is **optional**
    - `[pre/post]` specifies if the constraint shall be valid **before or after** execution of [method]
      - if this part is left away, it means, that the constraint shall be true all the time
    - `[inv]` indicates the declaration of an invariant, **invariants are valid for the lifetime of a class**
    - `[EXEC]` see below

- **EXEC**
  - either
    ```
      [*boolean op] [self.][@pre][st1] [#boolean op] [self.][@pre][st2] [...]
    ```
    where:
      0. `[self]` is fully optional and references to the class itsself
      1. `[*boolean op]` is one of the following: *not, and, or, implies, equals, xor* or left away
      2. `[st1]` is either a method call returning a value or a variable
      3. `[@pre]` is optional and addresses the value before evaluation of the statement
      4. `[#boolean op]` is one of the following: *< / > / => / =< / == / !=*
      5. `[st2]` is either a method call returning a value or a variable
      - **parts *3*, *4* and *5* are optional and can be chained**
  - or a "value assignment" following OCL syntax (*not, and, or, implies, equals, xor*)
    - instead of `=` you use `equals`
    - **there is no such thing as a "value assignment" in OCL, the value assignment is expressed indirect by "the variable should have the value xy in the end"!**

- pre- / postconditions
  - it is possible to specify the the time window of validity the constraint describes

-  pre/post conditions can describe temporal aspects
    - `[id]@pre` represents the attribute id **before** the operation
    - `[id]@result` result of the operation immediately after the execution

- values are assigned with `[assigned to] = [assigned from]` (Java syntax)

##### OCL-Collection
- the OCL-type collection is the generic superclass of a collection of objects of the type `T`
- subclasses of the *collection*  are:
  - ***set***: Set in the mathematical sense. Every element can appear only once
    - in class diagram: navigation along a single *one to many* association
    - ***multiset***: *many-to-many* associations
  - ***bag***: A collection, in which elements can appear more than once (also called multiset)
    - in class diagram: navigation along a couple of *one to many* associations
  - ***sequence***: A multiset, in which the elements are ordered
    - in class diagram: navigation along a single *one to many* with the association labeled as `{ordered}`
###### operations on collections
- `[collection]->[operation(arguments)]`
  where:
  - `[collection]` is the collection the operation is called on
  - `->` is the call indicator, chaining is possible eg. `coll1->asSet->size`
  - `[operation(arguments)]` is one of the following:
    - `size`: Integer<br>
      Number of elements in the collection
    - `includes(o:OclAny)`: Boolean<br>
      True, if the element o is in the collection
    - `count(o:OclAny)`: Integer<br>
      Counts how many times an element is contained in the collection
    - `isEmpty`: Boolean<br>
      True, if the collection is empty
    - `notEmpty`: Boolean<br>
      True, if the collection is not empty
- the following operations produce a new collection:
    - `union(c1:Collection)`<br>
       Union with collection `c1`
    - `intersection(c2:Collection)`<br>
       intersection with Collection `c2`
    - `including(o:OclAny)`<br>
       Collection containing all elements of the Collection and element `o`
    - `select(expr:OclExpression)`<br>
    Subset of all elements of the collection, for which the OCL expression `expr` is true

- type conversions on collections
  - `asSet`: transforms a multiset into a set
  - `asBag`: transforms a set into a multiset
  - `asSequence`: transforms a set or multiset into a sequence
