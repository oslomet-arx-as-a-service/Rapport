### Preface
The purpose of this documentation is to give the reader a detailed description of each test, and how the test are implemented. This documentent is written with the expectation that the reader has basic programming and testing knowledge.

### Table of Content


### Goal
The goal for these tests is to ensure that the service and the clients functionalities, works as they are expected to work. This is also to ensure that in an event that a feature fails, the right error message shows up with a detailed explanation on what went wrong and how to correct the error.

### Tools
These are the tools the team used for testing:
  - #### Postman
    - The team used postman to craft network requests and send it towards the service end-points, in order to quickly test the service.
   
  - #### travis 
    - The team used travis to automate the continues delivery pipeline. Each new branch pushed to the repository is tested in a virtual environment and has to pass before being allowed to be merged in to the master branch.
  
  - #### code climate 
    - Code climate was used as a static code analyser that showed test coverage as well the maintainability the code.
    
  - #### snyk
    - Snyk is used to ensure that the dependencies used in the project does not have any vulnerabilities
    
  - #### JUnit
    - Used for unit testing for the service.
    
  - #### Spring boot starter test
    - Used to test our service web environment. Edge case testing to ensure that the correct error messages shows and for the integration testing.
    
  - #### unittest(Python)
    - Used for unit testing the python client.
    
  - #### Pytest
    - 
    
  - #### coverage.py
    - 
  
### Planning

From the star, the project team planned on unit testing and exploring the functionalities available in the ARX libraries.This will ensure a good understaing of the feature and make it easier to intergrate them in the service.

Thereafter the project team decided to use test driven development on both the service- and client-side. The plan was to unit test each new method and make it pass, before moving on with an integration test and thereafter system testing of the end-points. Having a stable service end-piont will make it possilbe to work with the client-side parallelly and as early as possible.

The project team decided on a test plan to ensure a stable build is always produced before merging with the master branch in the repository. The project team decided on which test methods to use, test method naming, repository merge rules and tools to use to enforce the merge rules. 

Travis and Code Climate was also planned to be used to ensure that a stable build is always produced.

### Execution
Ensuring a stable build is produced for each ending of a sprint is important, therefor testing was continuesly done throughtout the project. For each new feature implemented a unit test must follow before being allowed to be merged to the master branch. Integration testing is done after all features in a sprint is implemented. Finaly system testing and edge case testing was done to ensure that the service works properly and in an event of an error, show a detailed explaination of what occured as well as make sure the correct error is shown.

- #### Travis
  For every push to github a travis build is started, in this build a virtual machine will run the program along with all the test. Each test must pass for travis to give a passing grade, this passing grade is used to restrict merging unstable builds to the repository.
  
  <image of how travis looks /passing/failing>
  
  A set of script is written to instruct travis what do upon a passing build. One of these steps is running jacoco. Jacoco will created a report on the test coverage of the service which will be then sent by the travis script to Code Climate.
  
  <image of travis scripts>
  
  Jacoco has settings that tells it which classes to ignore when creating the test coverage report. These classes are ignored because they are not meant to be tested.
  
  <image of jacoco settings>
  
  
  
- #### Code Climate
 Code Climate is used as a static code analysis tool. For each new push to the repository a Code Climate build is started, in this build Code Climate scans the codes and reports back a list of issues it finds. Code Climate also gets a test coverage result from Travis which is then given a grade. The team used this grade to see if a new feature has been tested. The grade will decrease if a new feature is pushed to the repository without it being tested. 
 
 <images of code climate>

- ### Snyk
Snyk is used to check the dependencies used in the project for known vulnerabilities. A report is sent to the project team when a known vulnerability is detected. A dependencies with vulnerability is usual fixed by updating to the newest version. In a case where an update doesnt fix the vulnerabitily, the project team will look at the dependency and how it effects the project. Depending on the extent of the effect the team will either leave it be or completely replace the dependency.

<image of snyk>

### Test Phases <OBS! maybe this belongs in the appendixes>
#### Test Design
Test design is a process that describes “how” testing should be done. It includes processes for the identifying test cases by enumerating steps of the defined test conditions. The testing techniques defined in test strategy or plan is used for enumerating the steps.

#### Unit testing
Unit tests are tests that test individual units or components in the system in isolation. A unit could be a class or a even a stand alone function.

Definition by ISTQB

unit testing: See component testing.
component testing: The testing of individual software components.

#### Integration testing
Integrations tests that tests the level where individual units of the system are combined. The porpuse is to expose errors in the interactions between system units.

Definition by ISTQB

integration testing: Testing performed to expose defects in the interfaces and in the
interactions between integrated components or systems.

#### System testing
System tests are tests that verify that the whole system works to specification.

Definition by ISTQB
system testing: The process of testing an integrated system to verify that it meets specified requirements.

#### Acceptance testing
Acceptance tests are test that verify the systems compliance with business requirements. These are the tests that should verify that the user of the system is receiving the requested value.

Definition by ISTQB

acceptance testing: Formal testing with respect to user needs, requirements, and business processes conducted to determine whether or not a system satisfies the acceptance criteria and to enable the user, customers or other authorized entity to determine whether or not to accept the system.
#### Performance testing
Performance test are tests that itend to determine how a system performs. Important variables that are measured are:
- responsiveness
- stability

The team has primarily utilized these performance testing types:

- Load testing
  A type of performance test where the systems behaviors under increasing load is tested.
- Stress testing
  A type of performance test where the system behavior under extreme load is tested

  Due to the user requirements and expected usage of the system spike and endurance testing was not completed.
  - Endurance testing
    The ARXaaS system does not use a database that could become overloaded or use other external services that could degrade over time.
  - Spike testing
    The ARXaaS system is deployed in a container orchestration service (Nais) where spikes are managed by the service.

#### Static analysis

### ARXaaS

#### Design testing
#### Unit testing
#### Integration testing
#### System testing
#### Acceptance testing
#### Performance testing
#### Static analysis

### PyARXaaS
#### Design testing
#### Unit testing
#### Integration testing
#### System testing
#### Acceptance testing
#### Performance testing
#### Static analysis

### WebARXaaS
#### Acceptance testing


### Conclusion

### References
http://softwaretestingfundamentals.com/acceptance-testing/
