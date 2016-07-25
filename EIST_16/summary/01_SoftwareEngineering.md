# Software Engineering
- Software engineering is a collection of techniques, methodologies and tools that help with the production of
- _A high quality software system developed with a given budget before a given deadline while change occurs_
- Challenge: Dealing with **complexity** and **change**

## Writing Software is problem solving
- understanding the problem
- proposing a solution and plan
- engineering a system based on the proposed solution using a _good_ design
- its about dealing with **complexity**
  - creating abstractions and models
  - notations for abstraction

- its about dealing with change
  - requirements elicitation, analysis, design, implementations, validation of the system, delivery and maintenance  

## Models
- a model is an abstraction of a system
  - a system that no longer exists / an existing system / a future system to be built
- Models are used to describe software systems
  - ***object model*** what is the structure of the system
  - ***functional model*** what are the functions of the system
  - ***dynamic model*** how does the system react to external events
  - **A system model consists of: object model + functional model + dynamic model**
  - together these models are a **system model**
  - other models in software development:
    - task model
      - PERT Chart (dependencies of tasks),
      - schedule: describes how the activities can be accomplished by the end of the project
      - Organization chart: roles of the participants
    - issue model
      - what are the open issues?
      - what proposals do we have to close the issues?
      - what resolutions can be made?

## Software development is difficult
- The problem is usually ambiguous
- the requirements are often unclear and changing
- the problem domain (also called **application domain**) is usually complex
- the **solution domain** is complex too
- the development process is difficult to manage
- software (offers) are extreme flexible
- software is a discrete system
  - continuous systems have no hidden surprises
  - discrete systems can have hidden surprises!
- A large scale system should consist of modules, where a module is a subsystem on its own

- **Analysis**
  - unterstand the nature of the problem and break the problem into pieces
- **sythesis**
  - put the pieces together into a larger structure
- **techniques**
  - formal procedures for producing results (parallel: cooking recipe)
- **methodologies**
  - collection of techniques unifies by a philosophical approach (parallel: collection of cooking recipes that also says what to do when there is no salt)
- **tools**
  - instruments of automated systems to accomplish a technique
  - IDE / CASE



**Computer science vs. Engineering**
- the computer scientist
  - assumes techniques and tools have to be developed
  - proves theorems about algorithms
  - designs languages and grammars
  - has infinite time
- the engineer
  - develops a solution for a problem formulated by a client
  - uses computers, languages, techniques, tools
- the software engineer
  - works in multiple application domains
  - has only limited time
  - while changes occurs in a complex problem formulation and often also in the available technology

## dealing with complex problems
  - **Abstraction** (identification of classes and objects)
    - **DEF:** Classification of phenomena into concepts
    - group collection of objects to reduce complexity
    - allows to ignore unessential details
      - Abstraction as an **activity** "abstraction is a thought process where ideas are distanced from objects"
      - Abstraction as an **entity** "abstraction is the resulting idea of a thought process where an idea has been distanced from an object"
    - Ideas can be expressed with a model

  - **Decomposition** (modules, subsystems, packages)
    - "divide and conquer"
    - two major types of decomposition
      - ***functional decomposition***
        - the system can be decomposed into functions
        - functions can be decomposed into smaller functions
      - ***object-oriented decomposition***
        - the system is decomposed into classes ("objects")
        - classes can be decomposed into smaller classes
    - **functional decomposition**
      - the functionality is spread all over the system
        - source code is hard to understand
        - source code is complex and impossible to maintain
        - the user interface is often awkward and non-intuitive
      - consequence:
        - the maintainer must often understand the whole system before making a single change to the system
    - **object-oriented decomposition**
      - decompose a system by having a lot of subsystems
      - "looks beautiful from outside, a lot of mess inside"

  - **Hierarchy**
    - "part-of" hierarchy
    - "is-kind-of" hierarchy
    - models relationships between objects
  - **approach**
    - start with a description of the functionality of a system
    - then proceed to a description of its structure
- **Project types**
  - **greenfield engineering project**
    - a system like this never existed before, begin from scratch
  - **reengineering project**
    - reuse classes from prior existing systems
  - **interface engineering project**
    - rebuilding the interface (desktop -> mobile)
- **Concepts and Phenomena**
  - Phenomenon
    - an object in the world of a domain as you perceive it
  - concept
    - describes the common properties of a phenomena
  - A concept is a 3-tuple:
    - [name, purpose, members]

## **Modeling**
  - **DEF:** Development of abstractions to answer specific questions about a set of phenomena while ignoring irrelevant details
  - ***relationships***
    - Type <-> variable
    - Concept <-> phenomenon
    - class <-> object
  - ***Abstract data type***
    - a type whose implementation is hidden from the rest of the system
  - ***class***
     - an abstraction in the context of object oriented languages
     - a class encapsulates state and behavior
  - ***system***
    - a _system_ is an organized set of communicating part
      - natural systems
      - engineered system
  - ***systems, models and views***
    - a _model_ is an abstraction describing a system
    - a _view_ depicts selected aspects of the system
    - a _notation_ is a set of graphical or textural rules for depicting models and views
      - _informal notation_ aka _napkin design_
      - _formal notation_ for example _UML_
    - views and models of a complex system often overlap

## Object-oriented modeling
  - _**Application Domain**_
    - Process of analysis
    - the environment in which the system is operation
  - _**Solution Domain**_
    - process of solution finding
    - the technologies used to build the system
