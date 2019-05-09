# De-Identification


## Preface

## Table of Contents

## Introduction

De-Identification, Anonymization and Pseudonymization often confused and used with different intentions. There is a lack of clear definition of the terms. We have attempted to define the terms with guidance from our product owner.

De-Identification is a common term for reducing the probability that a person can be identified from a dataset. These datasets are commonly refered to as microdata datasets. Microdata datasets are datasets that provide information on a set of variables for individuals. In practical terms this means each row in the dataset represents a individual or entity. Summarizing microdata into aggregates is a common method to de-identify the data, but this result in high levels of information loss and hinders other researches from verify the aggregate or do additional research.

From [Statistical Disclosure Control: A Practice Guide](https://buildmedia.readthedocs.org/media/pdf/sdcpractice/latest/sdcpractice.pdf)
*"The aim of anonymizing microdata is to transform the datasets to achieve an “acceptable level” of disclosure risk. The
level of acceptability of disclosure risk and the need for anonymization are usually at the discretion of the data producer
and guided by legislation."*

De-identification is a critical component in research,  mainly because it protects the privacy of individuals because once de-identified, a data set is considered to no longer contain personal identifiable information(PII). If a dataset does not include PII its use or distribution does not violate any privacy laws such as GDPR[https://gdpr.eu/data-privacy/]

## Terminology

- Equivalence class

    Records in a dataset that have the same values on the quasi-identifiers.

- PII

    PII or Personal Identifiable Information is any data that can be used to clearly identify an individual.

- Masking

    the process of removing a variable or replacing it with pseudonymous or encrypted information.

- Variable

    column of values in a data set representing a set of attributes.

## De-identification overview

There are two main types of de-identification:
 - Anonymization
 - Pseudonymization

When De-Identifying a dataset there is always a trade-off to be had between *privacy* and *data utility*. i.e. How hard it is to identify a individual in the dataset (data  protection) and how much value can be extracted from the dataset (data utility). These two interest are always at odds when de-identifying.

We will briefly talk about the pseudonymization before moving on to Anonymization which has been the focus of the teams work.

 **Pseudonymization**
 Pseudonymization is a type of de-identification where the association between data and person is removed. It achieves this by introducing a new bi-directional mapping between a individual in the dataset and his or hers identifiers. Pseudonymization can be irreversible, in that case the mapping to the identifers are deleted or reversible. Pseudonymization is regarded as a weak form of de-identification as the identifiers have only been moved to a separate mapping.

 **Anonymization**
 Anonymization intends to irreversibly reduce the linkage between an individual and identifying information in a dataset. 

When anonymizing a datasets attributes(columns/fields) are categorized into the following categories:

- Identifying Attributes
    Attributes that are directly identifiable. e.g. phone number, email, full name, bank account number
- Quasi Identifying Attributes
    Attributes that while not directly identifiable could be when used with other information to identify a person. e.g. birth date, zipcode, workplace, gps location data
- Sensitive Attributes
    Sensitive Attributes is information that could be damaging if released about a person. e.g. voting, medical information, criminal record
- Insensitive Attributes
    These are all other attributes in the dataset. Data points that neither could identify or cause harm to a individual if released.

Additionally quasi identifying attributes are further categorized in the following categories:

- Categorical variables are values in a finite set. e.g. gender, religion, home state.

- Continuous variables are values in a infinite set. e.g. income, weight, height. Due to their intrinsic uniqueness they are often transformed into categorical variables when anonymizing

 Main anonymization techniques:

 - Generalization
    Reducing the precision of a attribute. e.g full date of birth becomes only month and year or home address becomes home state or even country.
 - Suppression
    Replacing a value in a dataset with a null value. full name becomes '*'
 - Micro-aggregation
    Sets of numeric attribute values can be transformed into a common value by user-specified aggregation functions.
 - Subsampling
    Releasing only a subset of the dataset instead of all the records

Reducing the risk of disclosure 
Several models have been implemented to prevent the different disclosure types. We will only introduce the most important here. For a full overview see [https://arx.deidentifier.org/overview/privacy-criteria/]


K-Anonymity[k-ANONYMITY: A MODEL FOR PROTECTING PRIVACY](https://www.worldscientific.com/doi/abs/10.1142/S0218488502001648)
K-Anonymity ensures that the information for each person contained in the dataset cannot be distinguished from at least k-1 individuals whose information also appears in the dataset.

L-Diversity
L-Diversity protects a dataset against attribute disclosure. It does this by ensuring that each sensitive attribute has at least "l" represented values in each *equivalence class*. Different variants exist which differ in how they measure diversity. More here[https://dl.acm.org/citation.cfm?doid=1217299.1217302]

T-Closeness
T-Closeness also protects a dataset against attribute disclosure. I ensures that the distributions of values of a sensitive attribute within each equivalence class must have a distance of not more than t to the distribution of the attribute values in the input dataset. Also for T-Closeness there are several variants which differs in the way they measure the distance. More here[https://ieeexplore.ieee.org/document/4221659]

#### Risk assessment
Re-Identification is the reverse of de-identification and is the primary threat addressed by laws and regulation[https://www.sciencedirect.com/science/article/pii/S1386505618307007?via%3Dihub#bib0110]. Quantifying risk of re-identification associated with a dataset is of high importance. The key aspect for re-identification is the uniqueness of quasi identifying attributes and the uniqueness of the combinations of the attributes. Quasi attributes can be linked with additional data in the dataset or from external datasets to identify individuals.

In the literature these are the three types of disclosures that are of importance[https://buildmedia.readthedocs.org/media/pdf/sdcpractice/latest/sdcpractice.pdf]

- Identity disclosure

    Occurs if an attacker associates a known individual with a data record. e.g. If the attacker uses external information to in combination with a dataset to identify a person in the dataset.

- Attribute disclosure

    Occurs if an attacker is able to learn some new information about a person based on the information in the dataset. e.g. If a dataset show all males over 60 in Oslo has been on unemployment benefits.

- Membership disclosure

    Occurs if an attacker can determine if a individual is in a specific dataset without being able to identify the specific record.


Three different threat scenarios are commonly used by researchers[https://www.sciencedirect.com/science/article/pii/S1386505618307007?via%3Dihub#bib0110]

- Prosecutor attack model
    Under this model the attacker is assumed to a target specific individual and know data concerning the individual is present in the dttps://www.worldscientific.com/doi/abs/10.1142/S0218488502001648 attack can be calculatttps://www.worldscientific.com/doi/abs/10.1142/S0218488502001648of the records in the dataset.ttps://www.worldscientific.com/doi/abs/10.1142/S0218488502001648
- Journalist attack model
    Under this model the attacker is assumed to target an arbitrary individual without knowing if the individual is present in the dataset. Regarded as a more realistic model than the prosecutor model.
- Marketer attack model
    Under this model the attacker is assumed to aim at re-identifying as many individuals as possible. The risk of a successful attack can be expressed as the expected average number of re-identified individuals from the dataset.


##

### References
personal data: https://gdpr-info.eu/issues/personal-data/
K-anonymity: https://www.worldscientific.com/doi/abs/10.1142/S0218488502001648
L-diversity: https://dl.acm.org/citation.cfm?doid=1217299.1217302
T-closeness: https://ieeexplore.ieee.org/document/4221659

