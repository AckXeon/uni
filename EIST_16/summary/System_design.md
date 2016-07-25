\# includes L8

# System design

## Overview of system design
- design is difficult
  - *analysis*: focuses on the application domain
  - *design* focuses on the solution domain
    - the solution domain changes very rapidly ("halftime knowledge in software engineering: 3-5 years")
    - design knowledge is a moving target
    - *design window*: time in which design decisions have to be made

## System design: 8 issues
1) Identify design goals
    - additional nonfuctional requirements
    - design trade-offs
2) subsystem decomposition
    - layers vs. partitions
    - architectural style
    - coherence & coupling
3) identify concurrency
    - identification of parallelism (processes, threads)
4) hardware / software mapping
    - identification of nodes
    - special purpose systems
    - buy vs. build
    - network connectivity
5) persistent data management
    - storing persistent objects
    - filesystem vs. database
6) global resource handling
    - access control
    - ACL (access control list (eg. unix: own / group / all) vs. capabilities
    - security
7) software control
    - monolithic
    - event-driven
    - concurrent processes
8) boundary conditions
    - initialization
    - termination
    - failure

## from analysis to system design
| source | goal |
|---|---|
| nonfunctional requirements | 1. design goals |
| functional model | 2. subsystem decomposition |
| dynamic model | 3. identify concurrency |
| object model | 4. hardware / software mapping |
| object model | 5. persistent data management |
| dynamic model | 6. global resource handling |
| dynamic model | 7. software control |
| functional requirements | 8. boundary conditions |

### 1) design goals
- design goals govern the system design activities
- any nonfunctional requirement is a deign goal
- additional stakeholder goals are formulated with respect to
  - design methodology
  - design metrics
  - implementation goals
- design goals often conflict
  - typical design goal trade offs

| typical design trade offs: | |
| --- | --- |
| functionality | vs. usability |
| cost | vs. robustness |
| efficiency | vs. portability |
| rapid development | vs. functionality |
| cost | vs. reusability |
| backward compatibility | vs. readability |

### 2) subsystem decomposition
#### subsystems and services
- **subsystem**
  - collection of classes, associations, operations, events that are closely interrelated with each other
  - the classes in the object model are the "seeds" for subsystems
- **service**
  - a group of externally visible operations provided by a subsystem (aka *subsystem interface*)
  - the use cases in the functional model provide the "seeds" for the services
- **subsystem interface**
  - a set of fully typed UML operations
  - specifies the interaction and information flow from and to subsystem boundaries, but not inside the subsystem
  - refinement of service, should be well-defines and small
  - subsystem interfaces are defined during object design
- **applications programmer's interface (API)**
  - the API is the specification of the subsystem interface in a specific programmin language
  - APIs are defined during implementation
- **subsystem interface object**
  - the set of public operations provided by a subsystem
##### Coupling and coherence of subsystems
- goal: reduce system complexity while allowing change
- *coherence / cohesion* measures dependency among classes
  - *high coherence*: the classes and subsystem perform similar tasks and are related to each other via many associations
  - *low coherence*: lots of miscellaneous and auxiliary classes, almost no associations
- *coupling* measures dependency among subsystems
  - *high coupling*: changes to one subsystem will have high impact on other subsystems
  - *low coupling*: a change in one subsystem does not affect any other subsystems
- system design goal: **high coherence and low coupling**
  - *high coherence* can be achieved if most of the interaction is within subsystems, rather than accross subsystem boundaries
  - *low coupling* can be achieved if a calling class does not need to know anything about the internals of the called class (principle of *information hiding*) <br><br>

**subsystem decomposition**: Identification of subsystems, services, and their relationship to each other <br>
**architectural style**: a pattern for a subsystem decomposition<br>
**software architecture**: instance of an architectural style<br>

#### architecture styles
- **elements of an architectural style**:
  - *components* (subsystems)
    - computational units with a specified interface
  - *connectors*
    - interactions between the components (subsystems) <br> <br>
- **layered architectural style**
  - a layer is a subsystem that provides a service to another subsystem with restrictions:
    - a layer only depends on services from lower layers
    - a layer has no knowledge of higher layers
  - in terms of components and connectors:
    - Subsystems (Components)
      - Group of subtasks which implement an abstraction at some layer in the hierarchy
    - Connectors
      - Protocols that define how the layers interact
  - two major dependencies between layers
    - *depends on* relationship (compile time dependency)
    - *calls* hierarchy (runtime dependency)
  - two layered architectural styles
    - closed:
      - a layer can only call operations from the layer below
      - goals: maintainability, flexibility
    - open architecture
      - any layer can call any layer from below
      - goal: high performance
- **client server**
  - special case of layered architectural style
  - one or more servers provide services to instances of subsystems, called clients
  - the client knows the interface of the server, but the server doesn't know the interface of the client
  - goals: portability, location-transparency, high performance, scalability, flexibility, reliability
  - problem: doesn't offer peer to peer
  - in terms of components and connectors:
    - Subsystems (Components)
      - subsystems are independent processes
      - servers provide specific services
      - clients use these services
    - Connectors
      - Data streams, typically over a communication network

- **peer to peer architectural style**
  - the p2p architectural style is a generalization of the client/server architectural style: clients can be servers and servers clients (*peers*)

  - in terms of components and connectors:
    - Subsystems (Components)
      - model, views, controllers
    - Connectors
      - **events**: chance-propagation mechanism via *events* ensures consistency between user interface and model
      - **Method calls**:
        - Read Data(), Initiate Operation(), Update()
        - If the user changes the model through the controller of one view (UpdateView()), the other views will be updated automatically
- **repository architectural style**
  - idea: support a collection of independent that work cooperatively on a common data structure called the repository
  - Subsystems access and modify data from the repository. The subsystems are loosely coupled (they interact only through the repository)

#### design metrics
##### cohesion and coupling measure interdependence
- *cohesion* measures interdependence of the elements in one subsystem
- *coupling* measures interdependence between different subsystems <br>

achieving **high cohesion and low coupling**:
| high cohesion | low coupling |
| --- | --- |
|Operations work on same data | Small interfaces |
| Operations implement a common abstraction or service | Information hiding |
| | No global data |
| | Interactions are mostly within the subsystem rather than across subsystem boundaries |


### 3) concurrency
- Used to address nonfunctional requirements such as: Performance, Response time, latency, availability
- Two objects are *inherently concurrent* if they can receive events at the same time without interacting
  - Good source for identification: Objects in a sequence diagram that are independent from each other
- Inherently concurrent objects can be assigned to separate threads of control
  - Objects with mutual exclusive activity can be folded into a single thread of control

#### thread of control
- a thread of control is a path through a set of state diagrams where only a single object is active at any time
  - a thread remains withing a state until the object sends an event to a second object, which then becomes active
  - *thread splitting*: object does a non-blocking send of an event to another object, so it does not wait
- concurrent threads can lead to *race conditions*

#### implementing concurrency
- physical concurrency
  - threads provided by hardware
- logical concurrency
  - Threads are provided by software (usually provided by threads packages)

- In both cases, - physical concurrency as well as logical concurrency - we have to solve the scheduling of the threads
- Concurrency introduces problems such as starvation, deadlocks, fairness

### 4) Hardware / software mapping
- this system design activity addresses two questions:
  - how to realize the subsystems, hard or software?
  - how will the object model be mapped onto the chosen hard / software

#### hardware software mapping difficulties
- much of the difficulty of designing a system comes from addressing externally-imposed constraints of hard / software
#### hardware software mapping in uml
- a *UML component* is a building block of the system.
  - It is represented as a rectangle with a tabbed rectangle symbol inside
- components have different lifetimes
  - eg. classes or associations only exist at design time
  - eg. source code or pointers exist at compile time
- The Hardware/Software Mapping addresses dependencies and distribution issues of UML components during system design

### 5) data management
- all classes of type entity in the system model need to be persistent
  - *Persistency:*: a class is persistent, if the values if their attributes have a lifetime beyond a single execution
- persistent classes are realized with:
  - file systems (if the data is used by multiple readers, but just a single writer at the same time)
  - database systems (if there are multiple concurrent readers and writers)

#### mapping an object model to a relational database
- UM models can be mapped to relational databases
  - some degradation appears, because all UML constructs have to be mapped onto a single relational database construct, the ***table***
- mapping of classes, attributes and associations
  - Each *class* is mapped to a *table*
  - Each *class attribute* is mapped onto a *column* in the table
  - An *instance* of a class represents a *row* in the table
  - A *many-to-many association* is mapped into its own *table*


### 6) global resource handling
- addresses access control
- describes access rights for different classes of actors

#### defining access control
- In multi-user systems different actors usually have different access rights to functions and data
- how are these access rights modeled?
  - During analysis we model access rights by associating use cases with the actors
  - During system design we model access rights by determining which objects are shared among actors
    - For this purpose we introduce the *access matrix*

#### access matrix
- An *access matrix* models the access of actors on classes
  - The *rows* of the matrix represents the *actors* of the system
  - The *column* represent *classes* whose access we want to control
- ***Access Right***: An entry in the access matrix. It lists the operations that can be executed by the actor on instances of the class

- access matrix implementations
  - ***global access table***
    - represents every non-empty cell in the matrix as a triple <actor, class, operation>
  - ***access control list***
    - Associates a list of (actor,operation) pairs with the class being accessed
    - Every time an instance of this class is accessed, the access list is checked for the corresponding actor and operation
  - ***capability***
    - associates a (class, operation) pair with a actor
    - A capability allows an actor to gain control access to an object of the class by calling one of the class operations described in the capability
