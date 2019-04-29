### Preface
The purpose of this documentation is to give the reader a detailed description of each test, and how the test are implemented. This documentent is written with the expectation that the reader has basic programming and testing knowledge.

### Table of Content


### Goal
The goal for these tests is to ensure that the service and the clients functionalities, works as they are expected to work. This is also to ensure that in an event that a feature fails, the right error message shows up with a detailed explaination on what went wrong and how to correct the error.

Additionaly these tests were used to fullfil a test driven development work flow. As well as help ensure a agile work flow where each new feature has been tested and is stable before moving on to a new feature is implemented.

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
    
  - #### Spring test libraries
    - Used to test our service web environment. Edge case testing to ensure that the correct error messages shows and for the integration testing.
    
  - #### unittest(Python)
    - Used for unit testing the python client.
    
  - #### Pytest
    - 
    
  - #### coverage.py
    - 
  
### Planning

### Execution

### Client testing

### Service testing

### Security

### Performance testing

### Conclusion
