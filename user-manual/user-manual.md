
### Front page

### Preface

The purpose of this document is to give the reader a step-by-step guide on how to start the service, and how to use the clients. The user guides are written with the expectation that the end user is a data scientist or a person that has basic programming knowledge.

### ARXaaS service

#### Introduction

This documentaion contains a step-by-step guide on how to start the service. The service application is available as docker image and java archive file(jar). These files can be downloaded form docker hub and maven central.

    - The API doucmentaion can be found here: https://oslomet-arx-as-a-service.github.io/ARXaaS/#analyze-controller 
    - The javadoc can be found here: https://javadoc.io/doc/no.oslomet/arxaas/0.3.2-RELEASE

#### Manual, set up steps
#### Running the service locally
##### Run the service on localhost as a Docker container
Make sure that you have docker installed. Docker can be found here: https://www.docker.com/products/docker-hub

 1. Make sure Docker Desktop is running.
 2. Open the command-line interpreter and pull the Docker image

        docker pull arxaas/aaas

 3. Run the Docker

        docker run arxaas/aaas

##### Run the service on localhost from jar (download ARXaaS executable jar from Maven and execute it)
 Make that you have the latest version of java installed before going through these steps.
 
  1. Go to https://search.maven.org/search?q=g:no.oslomet and download the latest version of ARXaaS
  2. Open the command-line interpreter and run the jar file
        java -jar <path to jar>
  
#### Https configuration.
#### Troubleshooting
#### Error description.

### PyARXaaS client

### WebARXaaS client

### Statistics
- Stress
- Metrics dashboard
