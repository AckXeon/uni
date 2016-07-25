\# includes L17, L18

# Testing

## Terminology
- Failure
 - Any deviation of the observed behavior from the specific behavior
- Erroneous state (Error)
 - The system is in a state such that further processing by the system can lead to failure
- Fault
 - A mechanical or algorithmic cause of an error ("bug")
- Validation
 - Activity of checking for deviations between the observed behavior of a system and its specification

### types of misbehavior
- Algorithmic fault
 - missing check for null, ...
- Mechanical fault (hard to find)
 - missing protection mechanisms, ...
- errors
 - wrong user input, ...

### fault handling
- fault avoidance
 - use methodology to reduce complexity
 - apply verification to prevent algorithmic faults
- fault detection
 - testing, debugging, monitoring
- Fault tolerance
 - exception handling<br>
<img src="pics/taxforfaulthandling.png" width="300">

### Observations
- Its impossible to completely test a system
 - practical and theoretical limitations
- Testing can only show the presence of bugs, not the absence
- testing is expensive
- for testing its important to:
 - understand the system
 - have application and solution domain knowledge
 - have knowledge of testing methods
 - have the skill to apply these
- testing should be best done by independent testers

### Test model
- the test model consolidates all the test related decisions into one package
- the test model contains:
 - a test driver
 - test case
 - input data
 - oracle (expected output)
 - test harness
   - framework for testing where the test are run

### automated testing
- Manually (run by dev himself)
- Automatically (test triggered by for example changes in the code)

### model based testing
- the system model is used for the generation of the test model
- def: system under test
 - part of the system that is being tested

## object-oriented test modeling
- start with the system model
- system contains the SUT
- SUT is not isolated
- test model is derived from the SUT
-
- test doubles:
 - 4 types of test doubles:
   - dummy objects
     - never actually used but passed around
     used to fill parameter lists
   - fake object
     - working implementation but usually contains a "shortcut"
   - stub
     - always same answer when invoced
   - mock objects
     - mimic behavior

## Testing activities and corresponding models
- Developer part:
 - unit testing (from object design),
 -integration testing (from system design),
 - system testing (from requirement analysis)
- client part:
 - acceptance testing (from client expectations)

- unit testing
 - individual components
 - goal: confirm that the component is correct
- integration test
 - groups of subsystems are tested
- system testing
 - the entire system is tested
- acceptance testing
 - system is tested in the target environment

### static and dynamic analysis
- static analysis
 - hand execution by reading the source code
 - walk though by informal presentation to others
 - code inspection by formal presentation to others
 - automated tools that check for syntax, semantic errors, etc
 - cheaper that other testing methods
- dynamic testing
 - black box testing
    - focuses I/O behavior
    - goal: reduce number of test cases by equivalence patitioning
     - divide inputs into classes (legal / illegal input, ...)
     - chooses tests for these classes (below, in, above range,.   )
 - white box testing
   - thoroughness. Every component is executed at least once
   - four types of white-box testing
     - statement testing
     - loop testing
     - path testing
     - branch testing
   - statement testing (algebraic testing)
     - test each statement
   - loop testing
     -loop can be executed exactly once, more than onnce, skipped completely
   - path testing
     - makes sure that all paths are executed once
   - branch testing
     - ensure that each outcome in a condition is tested at least once

 - comparisons slide 48
   - whitebox testing
     - potentially infinite number of paths
     - often test what ist done, not what should be done
   - blackbox testing
     - potential combinatorical explosion of test cases
     - does not discover extraneous use cases
   - both types of testing needed

### integration testing
- main goal: test the subsystems and the interaction of the subsystems (test the interfaces)
- integration testing strategy
 - big bang integration
 - bottom up testing
 - top down testing
 - sandwich testing
 - vertical testing

- Terminology
 - driver
   - a component that calls the tested unit
 - stub

- big bang approach
 - missing time leads to only one test of the whole system (bad)
- bottom up testing strategy
 - the subsystems in the lowest layer of the call hierarchy are tested individually
 - the subsystems  above are tested
 - repeated until in top layer (all subsystems tested)
 - makes sure all subsystems being tested rely on correct working subsystems
- top down testing strategy
 - start with testing the top layer
 - test "trough" the subsystems until bottom layer is reached
- sandwich testing strategy
 - define are target layer
 - the system is viewed as having three layers
   - test the layer above and below the SUT
   - the SUT itself
 - test the three layers individually
- top down integration testing
 - pros
   - test cases can be defined in terms of functionality of the system
   - no drivers needed
 - cons
   - stubs are needed
   - writing stubs is difficult, a large nuber of stubs may be needed
- bottom up integration testing
 - pros
   - no stubs needed
   - useful for testing object oriented or realtime systems

- sandwich testing
 - pros
   - top and bottom layer testing can be done in parallel
 - cons

### horizontal integration
- steps in horizontal testing
 - select a component
 - fix peliminary fix-up requirement (stubs, ...)
 - test functional requirement
 . test subsystem decomposition
 - test non-funtional requirements
 - keep records of your test
 - repeat the steps

- risks in horizontal integration testing
 - the higher the complexity, the more difficult the integration of the components
 - late integration of components has a high risk of failure

### vertical integration
 - build as early and frequently as possible
   - in scenario driven design and scrum, ...
 - advantages
   - there is always an executable version of the system
   - there is a good overview of the project status

- continuous integration
 - team members integrate their work frequently
 . each integration is verified by an automated build

### system testing
- functional testing
- performance testing
- acceptance testing
 - alpha test, beta test

 ## Fault Tolerance

 ### Exception handling
 - Exception handling is a better way to deal with a failure than letting a system crash
   - but programmers must foresee the failure
 - Exceptions are a better way to give an error report to the caller
 - **robustness**: robustness is the ability of a system to come with errors during execution and cope with erroneous input
 - **unchecked exception**: it is the responsibility of the caller to check for erroneous input
 -**checked exception**: it is the responsibility of the callee to check for erroneous input
 - robustness is a good design goal

 - refactoring steps to replace error code
   - find the methods that use error code
   - replace error code with checked / unchecked exception code

 - what constitutes successful testing
   - the purpose of testing is the generation of failures
   - "the test is successful, if it generates a failure"

 Terminology
 - **Failure**: any deviation of the observed behavior from the specified behavior
 - **fault**: the mechanical or algorithmical cause of an error
 - **error**: the system is in a state such that fuŕther processing by the system can lead to a failure
 - **verification**: Activity that checks if the observed behavior complies with the specified behavior of a system
 - **validation**: Activity that checks if the observed behavior meets the needs informally expressed by a stakeholder

 ### JUnit
 - A java framework for running unit tests
 - the newest version of JUnit uses Java **annotations** and **assertions**
 - JUnit is good for testing the state of a SUT
 - limitations:
   - JUnit does not provide mechanisms to test a specific sequence of operations

 ### Object-oriented model based testing
 - the test model is derived from the system model (which contains the SUT)
 - objects of this model are called test doubles
 - *mock objects* are used to mimic the behavior of a real object
