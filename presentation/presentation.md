### Front page
### Preface
This is a summary presentation of the product we have developed. It's purpose is to give a short but complete overview of the project background, the product development process and finally the concrete solution developed.

### ToC
### Introduction
The terms data and dataset are used continuously throughout the documentation. Unless anything else is specified, the term refers to tabular data/datasets. The problem space is data anonymization, as such, when talking about data/datasets we are generally referring to population data.

### Presentation of the group
 - Sondre - IT
 Worked part time for NAV IT AI-lab since fall 2018. Main competence is Java and Python development, but has worked with web development in previously.
 - André
 - Julian
 - Viktor
 - Jeremiah

### Presentation of client
The Norwegian Labour and Welfare Administration (NAV) is the backbone of the Norwegian welfare state, administering a third of the national budget and servicing almost 2.8 million people through a range of schemes such as unemployment benefit, work assessment allowance, sickness benefit, pension, child benefit and cash-for-care benefit. 
In addition, NAV manages and retains stewardship of several important data sources containing information on its users and the services it provides. NAV IT is currently in the midst of a digital transformation, undergoing significant changes in team organization, work processes and harnessing new technologies.
Its use of data in the development of new and improved services is often contingent upon strict data privacy practices and its ability to innovate in a privacy-preserving manner.


Our client for this assignment is NAV IT Data og Innsikt. Data og Innsikt is a department within NAV IT. The department delivers the development of systems and operations of data storage, data processing, data access and analytics.

### Project background
AI Lab is a department in NAV IT Data og Innsikt, functioning as NAV ITs internal knowledge hub in machine learning and data science. One of the areas the team currently is handling is data anonymization. This area presents problems in both the legal and ethical domain, because of its close connection to personal data. 
Data anonymization is a large field with many projects worldwide. There are well established models and algorithms for both anonymization and analytics of data. AI Lab is currently utilizing both internal and external tools for data anonymization. One such tool is ARX, which is widely regarded as top-class anonymization software. ARX is an open source (Apache License, Version 2.0)  project distributed as a GUI application and as a Java JAR library. It is prominently used by large organizations to anonymize health and patient data.

ARX contains a large and powerful amount of functionality for data anonymization, but the interaction with said functionality is limited to either interaction with the GUI application or programmatically with the Java API provided by the JAR. Neither option is well suited to modern data science applications. 
Data science today is typically conducted within programming languages like Python and R. The data scientist develops scripts, notebooks and larger programs for extracting and analysing data. Early stage tasks typically include data cleaning and data transformation. Anonymisation may be viewed as such a data transformation task, but ARX currently does not integrate seamlessly into the typical Python/R-based data science workflow. 
Moreover, while ARX provides functionality and flexibility for a skilled user, the front-end arguably requires knowledge of technical concepts and methods in anonymisation above and beyond that of the typical developer and which requires a non-trivial investment of time to learn and understand.

The AI-lab has therefore requested the group to:
- Provide access to ARX functionality from modern data science toolsets and workflows
- Provide an extendable framework for making state-of-the-art anonymisation methods accessible to a wider audience in NAV IT by lowering the barriers to use.  

### The Product - ARX as a Service
ARX as a Service refers to the group of products that make up the ARX as a Service ecosystem. The center piece of this ecosystem is the micro service named ARXaaS. Addidtionally to ARXaaS there are two clients named PyARXaaS and WebARXaaS. These products provide Python and WEB usage of the service.

#### Current situation

Much of the literature, practices and frameworks in the de-identification space are targeted for distribution of medical data between researchers. NAV has a similar use case, but different in that the organization primarily is concerned with internal reuse of data. Every new usage of PII data in NAV has to go trough a Data Protection Impact Assessment or DPIA[https://www.datatilsynet.no/regelverk-og-verktoy/veiledere/vurdering-av-personvernkonsekvenser/]. This means that data scientist working in NAV AI-lab that wants to research a new possible use for some data has to go trough a lengthy assessment just to be able to inspect the data. A lot of time is spent on getting the necessary access to be able to do preliminary assessments of data. Often the data is gauged to be insufficient and the time spent on the DPIA is more or less wasted.

There are several products in the anonymization/de-identification space. But the tools fall mainly into two categories: 
 - Proprietary solutions that works as a "walled garden" with limited integration with other tooling
 - Open source projects built by and for researches

 Common to both categories is the fact that most solutions are mainly focused on Graphical user interfaces. There is limited support for integration and further development.

#### De-Identification
Following is a short descripion of the field of de-identification. For more in-depth explanations see the chapter De-Identification.

De-Identification is a common term for reducing the probability that a person can be identified from a dataset containing *personal identifiable information* or PII. In practical terms this means each record in the dataset represents a individual or entity. Summarizing dataset containing PII into aggregates is a common method to de-identify the data, but this result in high levels of information loss and hinders other researches from verify the aggregate or do additional research.

De-identification is a critical component in research. It permits sharing and using PII for secondary purposes by transforming the data util it can not longer be classified as PII.

From [Statistical Disclosure Control: A Practice Guide](https://buildmedia.readthedocs.org/media/pdf/sdcpractice/latest/sdcpractice.pdf)
*"The aim of anonymizing microdata is to transform the datasets to achieve an “acceptable level” of disclosure risk. The
level of acceptability of disclosure risk and the need for anonymization are usually at the discretion of the data producer
and guided by legislation."*

There exist several models for both quantifiable assess the disclosure risk for a given dataset and anonymize a dataset until it meets required risk thresholds


#### Solution description
The system will provide access to anonymization tools for data scientists at NAV IT. A data scientist should be able to anonymize tabular dataset based on user-specific configurations. Configurability includes privacy models, column attribute types and transformation models that determine how much data will be lost in the resulting anonymized dataset. 
A common use case would be in a workflow where the data scientist is manipulating a dataset, and requires dynamic analysis of the data anonymity metrics. Another use case could involve integrating the system in a data pipeline to provide data analytics and anonymization capabilities.

#### Deployment
The team developed in a complete CI/CD pipeline for the core components using the Travis CI platform. As the client wished that the finished product could be deployed to NAVs internal container orchestration solution Nais, the team setup their own kubernets kluster to continously deploy to in the first sprints until the product stabilized and deployment moved to Nais.

The deployment of a single merge to master for the main service goes through the following steps before it is deployed to the Nais platform. If there is any failures the deployment is stopped and the team is notified.

- Test
    The full test suite is with unit tests, integration tests and system tests are ran.

- Documentation
    API documentation for the HTTP endpoints are generated. This documentation is a combination of human written text and auto generated snippets of information about the various endpoints, accepted HTTP verbs, request and response body JSON structure.

- Packaging
    The service is packaged in different artifacts with different formats for the deployment and artifact hosting platforms. Main artifacts being Java JAR and docker.

- Deployment
    The packaged artifacts are deployed to different platforms and hosts. 
    - API Documentation is pushed to Github pages
    - Docker container is published to dockerhub
    - Source, Javadoc and class JARs are signed and published to maven central

After a new deployment has been completed both the teams internal Kubernetes cluster and NAVs Nais platform deploys the new service version.

Having a complete CI/CD setup from essentially day meant the team was continously gathering feedback on the product. It meant the client could use the features implemented as they where implemented and most importantly it meant the team had real-time information on the stability of the product.

### Conclusion

### References
personal data: https://gdpr-info.eu/issues/personal-data/
K-anonymity: https://www.worldscientific.com/doi/abs/10.1142/S0218488502001648
L-diversity: https://dl.acm.org/citation.cfm?doid=1217299.1217302
T-closeness: https://ieeexplore.ieee.org/document/4221659

### Word list

- Equivalence class

    Records in a dataset that have the same values on the quasi-identifiers.

- PII

    PII or Personal Identifiable Information is any data that can be used to clearly identify an individual. 
