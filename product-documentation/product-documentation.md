### Front page

### Preface
The purpose of this document is to give the reader a technical view of how the system has been build and the functionalities available in both the service and clients. This document also shows how the client works with the service. 

This document is written with the expectation of being used for working with operations, maintenance or future development, it is therefore expected that the reader has programming knowledge. For a better understanding of this document we recommend reading the presentation documentation first.

### Introduction

### ARXaaS REST web service

- Short presentation
- Technologies
#### Functionality

The service has 3 endpoints, to reach these end-points a client must use an HTTP POST call to a web address that is running the service. These endpoints are written using REST architecture[https://en.wikipedia.org/wiki/Representational_state_transfer]. The endpoint address is formed by using an annotation on each controller and method.

Example of a controller with a REST API endpoint:

```java

@RequestMapping("/api/analyze")
public class AnalyzationController {

    @PostMapping
    public RiskProfile getPayloadAnalyze(@Valid @RequestBody Request payload, HttpServletRequest request) {

```

By following the REST architecture the web address is form in this format
{web address of the service}/api/{function}. The resulting 3 end-points can then be reached by writing:
  - {web address of the service}/api/analyze
  - {web address of the service}/api/anonymize
  - {web address of the service}/api/hierarchy
  
When an end-point receives a request object, it gets validated if it is correctly formatted. When the validation process fails the end-point will send a response in the form of an error message. This validation works as an extra safety net, because the clients are designed to always send a request object with the correct format. When the validation process succeeds the service will send a response object containing a JSON body that gets unpacked and mapped by the clients. When the object is correctly formatted but contains invalid parameters, the end-point will send a response object containing the error message and how to correct the error.

#### Endpoints

This document will describe the functionality of each endpoint. This section will explain what each endpoint does and the response object it sends back to the user, as well as the different actions used with the request object sent to the endpoints.

##### Analyzation

This endpoint can be reached by writing "{web address of the service}/api/analyze" and is an HTTP POST method.

The endpoint receives a request object containing a data set to be analyzed and the attribute type list of the data set. The endpoint returns an object containing a risk profile that describes the re-identification risk and distribution of risk in a data set.

This endpoint creates an ARX data object with the data set and attribute type taken from the request object. This ARX data object is then analyzed against re-identification risk. After the analyzation process is done, a risk profile object containing a list of re-identification risk and distribution of risk is created and sent back as a response object.

The risk profile object contains a re-identification risk that describes how anonymous the data set is and the distribution of risk in the data set.

##### Anonymization

This endpoint can be reached by writing "{web address of the service}/api/anonymize" and is an HTTP POST method.

The endpoint receives a request object containing a data set to be anonymized, list of attribute types containing transformation models(hierarchy) and privacy models. This endpoint returns an object containing an anonymized data set, a risk profile, and an anonymization metrics.

This endpoint uses the data taken from the request object and anonymizes it against re-identification risk, based on the attribute types, privacy model and transformation model defined in the request object. After the anonymization process is done, the anonymized data set is then analyzed on how anonymous it is and creates a risk profile.

The anonymization metrics contain the transformation level used on each quasi-identifying attribute type, the meta data on the privacy models used to anonymize the data set and how long the anonymization process took in milliseconds.

##### Hierarchy

This endpoint can be reached by writing "{web address of the service}/api/hierarchy" and is an HTTP POST method.

The endpoint provides a interface to access ARX hierarchy builder features. This endpoint receives a request object
containing the dataset column to create the hierarchy for, the builder type and builder specific attributes. This endpoint
returns a response object containing the resulting hierarchy.

Currently the following builders are supported:

 - Redaction based
 - Interval based
 - Order based
 
 ##### Redaction based hierarchy
 
 This method builds hierarchies for categorical and non-categorical values using redaction. Dataset items are:

  1. aligned left-to-right or right-to-left,
  2. differences in length are filled with a padding character.
  3. Equally long values are redacted, character by character from left-to-right or right-to-left.
  
  ##### Interval based hierarchy 
  
  This method builds hierarchies for non-categorical values by mapping them into given intervals.
  
  ##### Order based hierarchy
  
  This method builds hierarchies for categorical and non-categorical values by ordering the dataset items and merging them into groups with the defined sizes.

#### Logging:

ARXaaS has logging implemented using log4j. For every data set that is analyzed and anonymized. The application provides metrics for received and completed requests. The log displays the size of the dataset, number of rows and columns, source IP, dataset bytesize, privacy model used, suppression limit and request processing time.

![](img/screenShotLog.png)

In the case of an error or exception, a full stack trace is printed to make debugging faster and more efficient.

![](img/ErrorLogStacktrace.png)

- Security/https settings
- Open source license

### Client side introduction


### PyARXaaS
PyARXaaS is a Python client package that provides abstractions for interacting with a ARXaaS instance. It is inspired by other client packages like PyGithub[https://github.com/PyGithub/PyGithub]. It  makes the integration of the risk analysis and de-identification functionality of ARXaaS as easy and intuitive as possible. The main user group of the package are data scientist that would be familiar and accustomed to work with data in Python. The main requirement from the client was that the anonymization functionality was to be made available in Python, this is the product which delivers on this requirement.

**The package features**
- ARXaaS class for configuration and calling actions.
- Dataset class for encapsulating and configuring a dataset
- Privacy Model classes for configuring the Privacy Models to use in anonymization.
- Easy integration with pandas DataFrames[https://pandas.pydata.org/]

#### Short presentation
#### Technologies
#### Functionality
#### Open source license
PyARXaaS is distributed under the MIT license. See LICENCE [https://github.com/oslomet-arx-as-a-service/PyARXaaS/blob/master/LICENSE]

### WebARXaaS

#### Short presentation

As a stretch goal, the employer wished for a way to quickly access the ARX functionality. It was therefore decided to implement an interactive web frontend, by taking advantage of the flexible REST API provided by the ARXaaS service. Making this client available will give the user the possibility to analyze or anonymize their data, without the need to install software on their local machine.

#### Technologies

The interactive Web service is implemented in React using multiple third-party frameworks in order to provide the best possible service

| Package     | Use                                                                                                                   |
| ------------| --------------------------------------------------------------------------------------------------------------------- |
| React       | React is a library for building interactive web user interfaces. It simplifies rendering content on the website and lets us split our code into many single-purpose components. |
| React-BootStrap | Open source toolkit for making flexible interfaces adaptable for a wide range of screen sizes including mobile phones. And gives the website a professional looking color scheme. |
| Papa Parse  | Powerful tool for parsing and building CSV files with JavaScript                                                      |

#### Functionality

All the functionality can be accessed through a single page application.
Where the two main functionalities is *analyzation* and *anonymization*.

##### DataImport

The data import step is mandatory whenever the user wish to analyze or anonymize the data.
To load data the user clicks the load button, and selects a *CSV* file.
Once the *CSV* file is loaded, a automatically generated section will be displayed, showing each of the attribute headers from the csv file below the data import area.

##### Analyzation

The analyzation feature requires that the user already has loaded a *CSV* file, and set the correct *attribute types*.
By pressing the *Analyze* button, the website will make a call to the backend service on `/api/analyzation` containing a JSON formatted payload, containing all the loaded data together with metadata.
Once the response is received back from the service it will render multiple tables bellow containing metrics describing the analyzation quality.

| Metric table          | Content                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------- |
| Reidentification risk | Contains percentage likelihood on various *re-identification risks*                                 |
| Risk interval         | Gives metrics on how large portions of the entries in the data which is affected by each risk range |

#### Anonymization

The anonymization feature requires that the user already loaded a *CSV* file, set the correct *attribute types*, and uploaded a *CSV* file containing a generalization hierarchy/transformation model for each of the *quasi-identifying* attributes.

By pressing the *Anonymize* button, the website will make a call to the backend service on `/api/anonymization` containing a JSON formatted payload, containing all the loaded data together with metadata.
Once the response is received back from the server, it will display tables containing the following tables.

| Metric table          | Content                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------- |
| Anonymization data    | The anonymized version of the dataset                                                               |
| Reidentification risk | Contains percentage likelihood on various *re-identification risks*                                 |
| Risk interval         | Gives metrics on how large portions of the entries in the data which is affected by each risk range |
| Process time          | The time spent by the backend anonymizing the request in milliseconds.                              |
| privacy models        | Containing metadata used by the serivce for each of the applied privacy models, and transformation model level used on the quasi-identifying attribute types.                     |

### Operations

This web application is built using *Node.js*. All the necessary dependencies for the project is specified inside the `package.json` file, in the root of the project directory.  
Note that the ARXaaS service must be available via a server or running localy, in order to be utilizing the *analyzation* and *anonymization* functionality.


### Future developments

#### Webarx
- Hierarchy builder
- More visualizations
- Upload the image on dockerhub

### Conclusion

