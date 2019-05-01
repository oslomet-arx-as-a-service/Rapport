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
ARX as a Service refers to the group of products that make up the ARX as a Service ecosystem. The center piece of this ecosystem is the micro service named ARXaaS. ARXaaS. Addidtionally to ARXaaS there are two client products that provides user friendly usage of the service.

#### Current situation
There are several products in the anonymization/de-identification space. But the tools fall mainly into two categories: 
 - Proprietary solutions that works as a "walled garden" with limited integration with other tooling
 - Open source projects built by and for researches

 Common to both categories is the fact that most solutions are mainly focused on Graphical user interfaces. There is limited support for integration and further development. 
#### The problem space - Anonymization
Anonymization, also referred to as de-identification is the process of reducing the probability that a person can be identified from a dataset.

Anonymizing datasets is a critical component in research. Mainly because it permits sharing and using PII [TODO define] for secondary purposes.

Secondary purposes are purposes that are not directly related to the primary use of the data (sending out newsletters, providing servies to the user, etc). 

There are two types of anonymization tequ

#### Solution description

The system will provide access to anonymization tools for data scientists at NAV IT. A data scientist should be able to anonymize tabular dataset based on user-specific configurations. Configurability includes privacy models, column attribute types and transformation models that determine how much data will be lost in the resulting anonymized dataset. 
A common use case would be in a workflow where the data scientist is manipulating a dataset, and requires dynamic analysis of the data’s anonymity metrics. Another use case could involve integrating the system in a data pipeline to provide data analytics and anonymization capabilities.
#### Deployment of solution

### Conclusion
