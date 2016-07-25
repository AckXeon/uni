# some terminology
- ***roundtrip engineering***
  - forward engineering + reverse engineering
- ***reengineering***
  - changing a software system after it has been reverse engineered
- ***falsification***
  - the act of disproving a theory or hypothesis

- ***inheritance in Java***
  - Realization of *specialization and generalization*
    - Definition of subclass
    - Java keyword: `extends`
  - Realization of *simple inheritance*
    - Overwriting of methods is not allowed
    - Java keyword: `final`
  - Realization of *implementation inheritance*
    - Overwriting of methods
    - No keyword necessary
    - Overwriting of methods is default in Java
  - Realization of *specification inheritance*
    - Specification of an interface
    - Java keywords: `abstract`, `interface`

- ***use of models***
  - *Communication*: The model provides a common vocabulary. A model is communicated informally (“conceptual model”)
    - Target is a human being (developer, end user)
  - *Analysis and Design*: Models enable developers to specify and reason about a future system
    - Target is a tool (CASE tool, compiler)
  - *Archival*: Compact representation for storing the design and rationale of an existing system
    - Target is the human (analysis, project manager).

- ***problem statement -> system model***
  - Analyze the problem statement
    - Elicit and identify ***functional requirements***
    - Elicit and identify ***nonfunctional requirements***
    - Identify ***constraints*** (*pseudo requirements*)
  - Build the ***functional model***:
    - Develop ***use cases*** to illustrate functional requirements
  - Build the ***dynamic model***:
    - Develop sequence diagrams to illustrate the interaction between objects
    - Develop state diagrams for objects with interesting behavior
  - Build the ***object model***:
    - Develop class diagrams for the structure of the system.

- ***project***
  - consists of:  
    - a start date and duration
    - a set of deliverables
    - a schedule
    -  all technical and managerial activities requeired to produce and deliver the deliverables
    - resources consumed by the activities
    - a project is managed by a ***project manager***
      - administers the resources
      - maintains accountability
      - makes sure the project goals are met

- ***functional organization***
  - in a functional organization people are grouped into departments, each addresses an activity

- ***communication event***
  - information exchange with defined objects and scopes
    - scheduled events: **planned communication**, eg. review, meeting
    - unscheduled events: **event-driven communication**, eg. request for change, clarification, bug report

- ***communication mechanism***
  - tool or procedure that can be used to deal with a communication event
    - **synchronous mechanism**: tool requires partner to be available at the same time
    - **asynchronous mechanism**: no need to be available at the same time as partner

- ***stages of a software project***
  1. conception
  2. definition
  3. start
  4. steady state
  5. termination

- ***role***
  - a role is a set of responsibilities

- ***authority***
  - the ability to make binding decisions between people and roles

- ***responsibility***
  - the commitment of a role to achieve specific results

- ***accountability***
  - tracking task performance to a specific person

- ***delegation***
  - binding a responsibility, assigned to one person, to another person ("let somebody else do the job")

- ***Software Configuration Management***
  - Software Configuration Management is a project function with the goal to make technical and managerial activities more effective

- ***continuous integration***
  - the goal is to have a working version of the software all the time during the project
  - The development team uses an automated workflow to periodically integrate and test all parts of the system to validate the correct functionality of a system after making changes
  - When a test does not pass, the team immediately turns their attention to finding and fixing the faults. This reduces integration problems, and ultimately speeds up development.

- ***continuous deployment***
  - The practice of continuously deploying successful software builds automatically to some environment, but not necessarily to actual users  the practice of continuously deploying successful builds automatically

- ***continuous delivery***
  - Continuous delivery implies continuous deployment and is the practice of ensuring that the software is continuously ready for release and deployed to actual customers

- ***software development activities***
  1) Requirement elicitation
  2) analysis
  3) system design
  4) detailed design (object design)
  5) implementation
  6) testing


- ***contract***
  - A contract is an exact specification of the interface of an object
  - A contract includes three types of constraints
    - Invariants
    - Preconditions (“rights”)
    - Postconditions (“obligations”)
