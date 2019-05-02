### Preface
The purpose of this documentation is to give the reader a detailed description of each test, and how the test are implemented. This documentent is written with the expectation that the reader has basic programming and testing knowledge, and has read the product documentation.

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

From the start, the project team planned on unit testing and exploring the functionalities available in the ARX libraries.This will ensure a good understaing of the feature and make it easier to intergrate them in the service.

Thereafter the project team decided to use test driven development on both the service- and client-side. The plan was to unit test each new method and make it pass, before moving on with an integration test and thereafter system testing of the end-points. Having a stable service end-piont will make it possilbe to work with the client-side parallelly and as early as possible.

The project team decided on a test plan to ensure a stable build is always produced before merging with the master branch in the version control host. The project team decided on which test methods to use, test method naming, version control host merge rules and tools to use to enforce the merge rules.

### Execution
Ensuring a stable build is produced for each ending of a sprint is important, therefor testing was continuesly done throughtout the project. For each new feature implemented a unit test must follow before being allowed to be merged to the master branch. Integration testing is done after all features in a sprint is implemented. Finaly system testing and edge case testing was done to ensure that the service works properly and in an event of an error, show a detailed explaination of what occured as well as make sure the correct error is shown.

- #### Travis
  For every push to github a travis job is started, in this job a virtual machine will run the program along with all the test. Each test must pass for travis to give a passing grade, this passing grade is used to restrict merging unstable builds to the version control host.
  
  <image of how travis looks /passing/failing>
  
  A set of script is written to instruct travis what do upon a passing job. One of these steps is running jacoco. Jacoco will created a report on the test coverage of the service which will be then sent by the travis script to Code Climate.
  
  <image of travis scripts>
  
  Jacoco has settings that tells it which classes to ignore when creating the test coverage report. These classes are ignored because they are not meant to be tested.
  
  <image of jacoco settings>
  
  
  
- #### Code Climate
 Code Climate is used as a static code analysis tool. For each new push to the version control host a Code Climate job is started, in this job Code Climate scans the codes and reports back a list of issues it finds. Code Climate also gets a test coverage result from Travis which is then given a grade. The team used this grade to see if a new feature has been tested. The grade will decrease if a new feature is pushed to the version control host without it being tested. 
 
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

The service has been unit tested, and integration tested using JUnit 4 and 5. System testing was done by using Spring boot starter test. 

#### Unit testing

Each method that integrates a feature from the ARXlibrary is unit tested. Along with these integrated methods, all the models and the most important components of the service has also been unit tested. 

<img of unit test code example>

Unit testing is done by using a test data and sending it in as a parameter. The resulting data is then checked by comparing it to an expected result.

<img of all unit test pass>

#### Integration testing

Integration testing is done on all the methods that uses the factory classes, and all the models used by the factory classes. A test object is generated and used as a parameter for integration testing. The resulting object from the integration tests is then checked if it managed to correcltly created the response model object.

<img of integration test example>

The integration is about making sure that the different methods from different classes can work together and create the correct data object.

Image of all passed integration test:

<img of all integration test pass>

#### System testing

System testing is done on 3 end points in the service. Spring boot starter test is used to start the service and a request object is then used. A respons object is then generated and checked if it is correclty created and if the values inside the object are correct.

<img example of system testing>

Edge case testing was also done by generating request object with incorrect or invalid data. The end-points are then expected to throw an error exception, this exception is then compared to with an expected exection as wells making sure that end-points sends a detailed description of the error message and how to correct the error.

<img of edge case testing>

Bellow is an image all passed the system test:

<img of edge cast and system test pass>

#### Performance testing
#### Static analysis

### PyARXaaS

#### Unit testing
#### Integration testing
#### System testing
#### Performance testing
#### Static analysis

### Acceptance testing

Acceptance testing was done by hosting a workshop. In this workshop both the product owner and three data scientist from NAV IT was present. The product owner and the participants followed a step by step guide on how to start and use our product. 

The main focus of this workshop was to show both the anonymization and analyzation features, as well as show the different data the user recieves from the process. Explore the different error messages was also tested to see if they were detailed enough on explaining the type of error and the solution to fixing the error. 

Feedback was collect on how to improve the service, as well as possible new features to be implemented.

<img of workshop>

#### WebARXaaS
The web api was shown in the workshop and was mainly tested for the analyzation and anonymization features.

<img of the web api>


### Conclusion

### References
http://softwaretestingfundamentals.com/acceptance-testing/
