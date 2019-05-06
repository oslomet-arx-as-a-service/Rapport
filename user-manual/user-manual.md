
### Front page

### Preface

The purpose of this document is to give the reader a step-by-step guide on how to start the service, and how to use the clients. The user guides are written with the expectation that the reader is a data scientist or a person that has basic programming knowledge.

### ARXaaS service

#### Introduction
This document contains a step-by-step guide on how to start the service, and how to configure it to run as a https. The service application is available as docker image and java archive file(jar). These files can be downloaded form docker hub and maven central.

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

##### Run the service on localhost from a jar (download ARXaaS executable jar from Maven and execute it)
 Make that you have the latest version of java installed before going through these steps.
  1. Go to https://search.maven.org/search?q=g:no.oslomet and download the latest version of ARXaaS
  2. Open the command-line interpreter and run the jar file
        
            java -jar <path to jar>
  
#### Https configuration.
Note that ARXaaS uses HTTP by default.


To enable https in ARXaaS, please apply one of the following Options.
The values following the '='s are for guidance.
Change them to match user specific settings.

#### Option 1(recommended): Run ARXaaS server with dynamic HTTPS parameters (Pass keystore with certificate(s) from host machine to Docker container AND pass HTTPS server configuration upon running Docker image)
##### NB: If your command application appears to stall after running this command, make sure to look for prompts from Docker concerning credential input
##### NB2: The -d option is not required. It runs the Docker container as a daemon process, allowing for it to run in the background without occupying the shell
```bash
docker run -d -v <absolute path to keystore on host machine>:<relative path from root directory in docker container to destination> -p 8080:8080 <docker image name> --server.ssl.key-store-type=<keystore type> --server.ssl.key-store=<relative path to keystore file from root directory in docker container> --server.ssl.key-store-password=<keystore password> --server.ssl.key-alias=<name/alias of certificate in keystore>
```
##### Working example
```bash
docker run -d -v C:/Users/vijo/git/ARXaaS/arxaas-keystore.p12:/app/arxaas-keystore.p12 -p 8080:8080 arxaas/aaas:latest --server.ssl.key-store-type=PKCS12 --server.ssl.key-store=/app/arxaas-keystore.p12 --server.ssl.key-store-password=password --server.ssl.key-alias=arxaas-https
```

#### Generating and correctly configuring a keystore for an ARXaaS project
##### NB3: Option 2 and 3 require a keystore file containing a certificate inside the Spring project's src/main/resources folder. Option 4 and 5  have the same requisites as option 2 and 3, plus compilation to jar / Docker image.
1. Create keystore and certificate. You will be prompted to set a password for the keystore
```bash
keytool -genkeypair -keystore <file name for new keystore, OPTIONAL: preceed file name with absolute path to destination directory> -storetype PKCS12 -alias <name for new certificate> -keyalg RSA -keysize 2048 -validity 360
```
2. OPTIONAL: Add more certificates to keystore
```bash
keytool -genkey -alias <name of new certificate> -keystore <path to keystore> -storetype PKCS12 -keyalg RSA -storepass <keystore password> -validity 730 -keysize 2048
```
##### NB4: For a non-dynamic HTTPS configuration, the keystore file should be placed in the Spring project's /src/main/resources folder. This is necessary for Spring to be able to find the certificate on the classpath with the settings that we have suggested

##### OPTIONAL: Verify that your certificate(s) are correctly stored inside the keystore
```bash
keytool -list -v -keystore <keystore file>
```

#### Option 2: Configure, compile and run server with hard coded, non-dynamic SSL configuration. (keystore file inside Spring project's src/main/resources folder required)
##### 1. Configuration should look like the following, change values after '='s to match user specific settings and uncomment the following settings from /src/main/resources/application.properties
```bash
server.ssl.key-store=classpath:<full keystore file name>
server.ssl.key-store-type=<keystore type (PKCS12 recommended)>
server.ssl.key-store-password=<keystore password>
server.ssl.key-alias=<name/alias of certificate in keystore>
```
##### 2. The Spring server can now be run with HTTPS support enabled
##### Docker: 
Build image
```bash
docker build -t <image name> <path to Dockerfile>
```
Run container
```bash
docker run -p 8080:8080 <image name>
```
##### Jar: 
Compile the project
```bash
mvn clean install
```
Run jar (after compiling it should be located inside the ARXaaS project's target folder) 
```bash
java -jar <path to jar>
```
#### The following options (3, 4 and 5) concern running the server with dynamic HTTPS configuration for static HTTPS keystore/certificate(s) (keystore file inside Spring project's src/main/resources folder)...

#### Option 3: ...from Spring project 
```bash
mvn spring-boot:run -Dserver.ssl.key-store-type=<keystore type> -Dserver.ssl.key-store=classpath:<keystore file name> -Dserver.ssl.key-store-password=<keystore password> -Dserver.ssl.key-alias=<name/alias of certificate in keystore>
```

#### Option 4: ...from jar file
```bash
java -jar aaas-0.1.1-RELEASE.jar --server.ssl.key-store-type=<keystore type> --server.ssl.key-store=classpath:<keystore file name> --server.ssl.key-store-password=<keystore password> --server.ssl.key-alias=<name/alias of certificate in keystore>
```

#### Option 5: ...from Docker image
```bash
docker run -p 8080:8080 -d arxaas/aaas --server.ssl.key-store-type=<keystore type> --server.ssl.key-store=classpath:<keystore file name> --server.ssl.key-store-password=<keystore password> --server.ssl.key-alias=<name/alias of certificate in keystore>
```


#### Troubleshooting
#### Error description.

### PyARXaaS client
#### Introduction
This document contains a step-by-step guide on how to start and use the Python Client. The python client was designed with the expectation that it would be used in Jupyter notebook, but it can be used on different IDE.

   - The API documentation can be found here: https://pyaaas.readthedocs.io/en/latest/
        
#### Installing PyARXaaS Client
        
        


### WebARXaaS client

### Statistics
- Stress
- Metrics dashboard
