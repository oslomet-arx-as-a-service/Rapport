### Preface
The purpose of this documentation is to give the reader a detailed description of each test, and how the test are implemented. This documentent is written with the expectation that the reader has basic programming and testing knowledge.

### Table of Content


### Goal
The goal for these tests is to ensure that the service and the clients functionalities, works as they are expected to work. This is also to ensure that in an event that a feature fails, the right error message shows up with a detailed explaination on what went wrong and how to correct the error.

Additionaly these tests were used to fullfil a test driven development work flow. The tests help ensure an agile work flow, where each new feature is tested and stable before moving on to a new implementation of features.

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

### Execution
Ensuring a stable build is produced for each ending of a sprint is important, therefor testing was continuesly done throughtout the project. For each new feature implemented a unit test must follow before being allowed to be merged to the master branch. Integration testing is done after all features in a sprint is implemented. Finaly edge case testing was done to ensure that the service shows a detailed explaination when an error occur as well as make sure the correct error is shown.

- #### Travis
  For every push to github a travis build is started, in this build a virtual machine will run the program along with all the test. Each test must pass for travis to give a passing grade, this passing grade is used to restrict merging unstable builds to the repository.
  
  <image of how travis looks /passing/failing>
  
  A set of script is written to instruct travis what do upon a passing build. One of these steps is running jacoco. Jacoco will created a report on the test coverage of the service which will be then sent by the travis script to Code Climate.
  
  <image of travis scripts>
  
  Jacoco has settings that tells it which classes to ignore when creating the test coverage report. These classes are ignored because they dont need to be tested.
  
  <image of jacoco settings>
  
  
  
- #### Code Climate
 Code Climate is used as a static code analysis tool. For each new push to the repository a Code Climate build is started, in this build Code Climate scans the codes and reports back a list of issues it finds. Code Climate also gets a test coverage result from Travis which is then given a grade. The team used this grade to see if a new feature has been tested. The grade will decrease if a new feature is pushed to the repository without it being tested. 
 
 <images of code climate>

- ### Snyk
 

### Client testing

### Service testing

### Security

### Performance testing

### Conclusion
