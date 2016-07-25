## Software Configuration Management
- Multiple Persons have to work on software that is changing
. more than one version of the software has to be supported
- manages evolving software systems
- an activity that allows to deal with different changes in different situations

- a set of management disciplines and techniques of initiating, evaluating and controlling change of a software project
- SCM activities
  - configuration item identification
  . change management
  - promotion management
  - branch management
  - release management
  - variant management
- no fixed order!

- roles:
 - configuration manager
 - change control board member
 - developer
 - auditor

- configuration item identification
  - modeling the system as a set of evolving components
- change management
  - management of change request
- promotion management
  - creation of versions for other devs
- branch management
  - management of concurrent development
- release management
  - creation of versions for clients and endusers
- variant management
  - management of coexisting versions

## Configuration Item Identification
- Configuration Item:
  - An aggregation of hard- / software (or both)
- Software configuration items are not only source files
- Selecting the right conf is a skill (similar to obj modeling)
  - find conf items
  - find relations between these
- **baseline**: A specification or product that has been reviewed, serves the basis for the further development
- **Change management**: handling of change requests
  - process:
    - the change is requested
    - the request is assessed
    - rejected or accepted
    - if accepted assigned to a dev
    - the implement is audited
- **change policy**: guarantee tat each promotion or release conforms to commonly accepted criteria
  - for example: "promotion policy", "release policy"
- **IEEE 828**
  - divides in
    - Programmers Directory
    - Master directory
    - Software directory
- **git terminology**
  - feature branch
  - development branch
  - master branch

## Baselines
- types of baselines:
  - product baseline
  - developmental baseline
  - functional baseline

## Branch management
- use branches to control concurrent development and explorations
- map functional requirements to feature branches
- important: minimize branch lifetime

## requirements for release management
- large and distributed software projects need to provide a development infrastructure with an integrated build management
  - regular builds from the master directory
  - automated execution of  tests
  - notifications
  - determination of code metrics
  - automated publishing
- the transition from source code to the executable application consists of a sequence
  1) Setting the required paths and libraries
  2) compiling source code
  3) copying source files
  4) setting file permissions
  5) packaging the applications
- performing these activities is time consuming and commonly produces errors
