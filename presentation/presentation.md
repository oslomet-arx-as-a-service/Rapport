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

#### The problem space - De-Identification
De-Identification is a common term for reducing the probability that a person can be identified from a dataset. Its opposite is re-identification or identifying a person in a generally assumed anonymous dataset. It is a critical component in research,mainly because it permits sharing and using *personal data* for secondary purposes. *Personal data* are any information which are related to an identified or identifiable natural person. Secondary purposes are purposes that are not directly related to the primary use of the data.

There are two main types of de-identification:
 - Anonymization
 - Pseudonymization

 De-Identification, Anonymization and Pseudonymization often confused and used with different intentions. There is a lack of clear definition of the terms. We have attempted to define the terms with guidance from our product owner.

When De-Identifying a dataset there is always a trade-off to be had between *privacy* and *data utility*. i.e. How hard it is to identify a individual in the dataset (data  protection) and how much value can be extracted from the dataset (data utility). These two interest are always at odds when de-identifying.

When de-identifying a datasets attributes (columns/fields) are categorized into the following categories:

- Identifying Attributes
    Attributes that are directly identifiable. e.g. phone number, email, full name, bank account number
- Quasi Identifying Attributes
    Attributes that while not directly identifiable could be when used with other information to identify a person. e.g. birth date, zipcode, workplace, gps location data
- Sensitive Attributes
    Sensitive Attributes is information that could be damaging if released about a person. e.g. voting, medical information, criminal record
- Insensitive Attributes
    These are all other attributes in the dataset. Data points that neither could identify or cause harm to a individual if released.

We will briefly talk about the pseudonymization before moving on to Anonymization which has been the focus of our work.

 **Pseudonymization**
 Pseudonymization is a type of de-identification where the association between data and person is removed. It achieves this by introducing a new bi-directional mapping between a individual in the dataset and his or hers identifiers. Pseudonymization can be irreversible, in that case the mapping to the identifers are deleted or reversible. Pseudonymization is regarded as a weak form of de-identification as the identifiers have only been moved to a separate mapping.

 **Anonymization**
 Anonymization intends to irreversibly reduce the linkage between an individual and identifying information in a dataset. It stands in contrast to pseudonymization which only replaces identifying information with tokens or masks it.

 Main anonymization techniques:

 - Generalization
    Reducing the precision of a attribute. e.g full date of birth becomes only month and year or home address becomes home state or even country.
 - Suppression
    Replacing a value in a dataset with a null value. full name becomes '*'
 - Micro-aggregation
    Sets of numeric attribute values can be transformed into a common value by user-specified aggregation functions.
 - Subsampling
    Releasing only a subset of the dataset instead of all the records

#### Risk assessment
Re-Identification is the reverse of de-identification and is the primary threat addressed by laws and regulation[https://www.sciencedirect.com/science/article/pii/S1386505618307007?via%3Dihub#bib0110]. Quantifying risk of re-identification associated with a dataset is of high importance. The key aspect for re-identification is the uniqueness of quasi identifying attributes and the uniqueness of the combinations of the attributes. Quasi attributes can be linked with additional data in the dataset or from external datasets to identify individuals.

Three different threat scenarios are commonly used by researchers[https://www.sciencedirect.com/science/article/pii/S1386505618307007?via%3Dihub#bib0110]

- Prosecutor attack model
    Under this model the attacker is assumed to a target specific individual and know data concerning the individual is present in the dataset. The risk of a successful attack can be calculated based on the distinguishably of the records in the dataset.
- Journalist attack model
    Under this model the attacker is assumed to target an arbitrary individual without knowing if the individual is present in the dataset. Regarded as a more realistic model than the prosecutor model.
- Marketer attack model
    Under this model the attacker is assumed to aim at re-identifying as many individuals as possible. The risk of a successful attack can be expressed as the expected average number of re-identified individuals from the dataset.

#### Solution description
The system will provide access to anonymization tools for data scientists at NAV IT. A data scientist should be able to anonymize tabular dataset based on user-specific configurations. Configurability includes privacy models, column attribute types and transformation models that determine how much data will be lost in the resulting anonymized dataset. 
A common use case would be in a workflow where the data scientist is manipulating a dataset, and requires dynamic analysis of the data anonymity metrics. Another use case could involve integrating the system in a data pipeline to provide data analytics and anonymization capabilities.

#### Deployment of solution

### Conclusion

### References
personal data: https://gdpr-info.eu/issues/personal-data/
