\# includes L19

# Project Organization and Communication

## Communication is critical
- in large system development efforts, there is more time spend in comm than dev
- software engineer need some soft skills
  - collaboration
  - presentation
  - management
  - technical writing
- **communication event**
  - information exchange with defined objects and scopes
  - scheduled: planned communication (team meeting,. ..)
  - unscheduled: event driven communication (problem report, ...)
- **communication mechanism**
  - tools to transmit information
  - synchronous
  - asynchronous (sender and receiver are not communication at the same time)<br>
<img src=pics/communication.png" width="400">

### communication events
**planned communication events**
- problem definition
  - present goals, requirements, constraints
- project review
  - assess status. review system model
- client review
  - brief the client
- walkthrough
- inspection
- status review
- brainstorming
  - generate and evaluate a large number of solution for a problem
- release
  - baseline the result of a software development
- postmortem review

**unplanned communication events**
- request for clarification
- request for change
  - a participant reports a problem and proposes a solution
- issue resolution
  - selects single solution for a problem for which several solutions have been proposed, uses an issue tracker

### synchronous communication
- (smoke signals)
- hallway conversation
  - supports: unplanned conversations,request for clarification, request for change
  - pro: cheap, effective
  - con: misunderstandings, information loss
- meeting
  - supports: planned conversations, client review, project review, brainstorming, ...
  - pro: effective for issue resolution and consensus building
  - con: high cost, low bandwidth
- portal
  - supports: release, change requests, inspections
  - pro: provide the user with a hypertext metaphor: docs contain links to other docs
  - con: does not easily support rapidly evolving documents
- email
  - supports: release, change requests
  - pro: ideal for planning communication and announcements
  - cons: taken out of context
- newsgroup
  - supports: release, change request, brainstorming
  - pro: suited for discussion
  - con: primitive access control

## ***Project*** definition
- a project is an **undertaking**, **limited in time**, to **achieve a set of goals** that **require a concerted effort**
- a project includes:
  - a set of **deliverables** to a client
  - a **schedule**
  - technical and managerial **activities** to produce and deliver the deliverables
  - **resources** consumed by the activities
<img src=pics/project.png" width="400">

- laws of project management
  - projects progress quickly until they are ~90% complete
  - if project content is allowed to change freely, the change rate exceeds the progress rate
  - project teams detest progress reporting because it manifests their lack of progress
  - murphy's law:
    - "if something can go wrong, it will"
- what makes a project successful
<img src=pics/succ_project.png" width="400">

## Project organisation
- a project organization defines the relationships among resources, in particular the participants, in a project
<img src=pics/organisation.png" width="400">

- a project organization should define:
  - who decides
  - who reports their status to whom
  - who communicates with whom
- functional organization
  - in a functional organization people are grouped into departments, each addresses an activity
  - properties:
    - projects are pipelined through the departments
    - different departments have often identical needs
  - advantages:
    - members of a department have a good understanding of the function alrea they support
  - disadvantages
    - is is difficult to make major investments in equipment and facilities
    - there is a high chance of overlap

  - project based organization
    - in a project based organization people are assigned to a projects, addressing a problem to be solved within a specified time and budget
    - advantages
      - very responsive to new requirements
      - new people can be hired who are familiar with the problem / have special capabilities
    - disadvantages
      - teams cannot be assembled rapidly
      - because there are no "predefined lines", roles and responsibilities have to be defined at the beginning of the project

  - matrix organization
    - in a matrix organization, people from different departments of a functional organization are assigned to work on one or more projects
    - people are usually assigned to multiple projects (<100% of their time per project)
    - advantages
      - teams for projects can be assemble repodöy from the existing line organization
      - rare expertise can be applied to multiple projects
      - consistent reporting and decision procedures can be used for projects of the same type
    - disadvantages
      - participants are usually not familiar with each other
      - participants must get used to each other
      - participants have different working styles

    - challenges
      - team members work on multiple projects which have competing demands for their time
      - team members work for two bosses, which have different focuses
      - multiple work procedures and reporting systems are used

  - when to use functional organization?
    - projects with high degree of certainty, stability, uniformity and repetition
      - requires little communication, role definitions are clear
  - when to use project-based organization
    - the project hat a high degree of unclarity
      - open comm needed
      - roles are defined on project basis
    - requirements are changing during development

  - organization and communication:
  <img src=pics/organizationUML.png" width="400">

## Roles in Software Organization
- **Role**
  - a role defines a set of responsibilities
  - typical roles in software organizations:
    <img src=pics/roles.png" width="400">

- **responsibilities** are assigned to roles, roles are assigned to people
- possible mappings of roles to participant
  - **one to one**
    - ideal, but rare
  - **many to few** (<- most of the time)
    - each project member has multiple roles
    - danger of over-commitment
    - need for load balancing
  - **many to "too-many"**
    - some people don't have significant roles
    - lack of accountability
    - loosing touch with project
- Key concepts for mapping roles to people
  - **authority**
    - the ability to make binding decisions between people and roles
  - **responsibility**
    - the commitment of a role to achieve specific results
  - **accountability**
    - tracking task performance to a specific person
  - **delegation**
    - binding a responsibility assigned to one person to another person ("let somebody else do the job")
    - three reasons for delegation
      - time management
      - expertise
      - training
    - you can delegate authority, but not responsibility. You can only share responsibility.

### Project: activities, tasks and functions
<img src=pics/project_af.png" width="400">
- activity diagrams (prior PERT-chart)
<img src=pics/house.png" width="400">
<img src=pics/uml_project.png" width="400">

- **activities**
  - major unit of work
  - culminates in major project milestones
  - activities are often grouped
  - allows separation of concerns

- **task**
  - a task describes the smallest amount of work tracked by the project manager
  - typically 3-10 days of effort
  - tasks are decomposed into sizes, that allow monitoring. Finding the appropriate size is essential.
  - a task is specifies by a work package
    - description of the work to be done
    - preconditions for starting, duration, required resources
    - risks involved
  - a task must have a completion criteria

- model of tasks, activities, roles, work products and packages
<img src=pics/task.png" width="400">


### simple dynamic model of a project
- every project has at least 5 states
  - **conception** - the idea is born
  - **definition** - a plan is developed
  - **start** - teams are formed
  - **steady state** - the work is being done
  - **termination** - the project is being finished
- UML model:
<img src=pics/states_project.png" width="400">
- **common mistakes**
  - project manager skipping the start phase
    - reasons for skipping
      - because of time pressure
  - project manager skips the definition and start phase
    - reasons for skipping
      - known territory argument: "I've done this before, no need to waste time"
      - unknown territory argument
  - project manager jumps straight into the steady state phase after joining the project late
  - project manager cancels the termination phase
    - reasons for skipping
      - limited resources, ambitious deadlines
      - you leave the project to move on right to the next one

- how to be a good project manager:
  - don't assume anything
  - communicate clearly with your developers
  - acknowledge performance
  - view your developers as allies, not adversaries
  - be a leader

- stages of a software project:
<img src=pics/stages_1.png" width="400">
<img src=pics/stages_2.png" width="400">


#### Some structures:
<img src=pics/commStruc.png" width="400">
<img src=pics/descStruc.png" width="400">
<img src=pics/descStruc2.png" width="400">
<img src=pics/hierstruc.png" width="400">
<img src=pics/hierstruc2.png" width="400">
