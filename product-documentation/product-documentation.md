### Front page

### Preface

### ToC

### Introduction

### ARXaaS REST web service

- Short presentation
- Technologies
- Functionality
- Security/https settings

### Client side introduction

- PyARXaaS
- Short presentation
- Technologies
- Functionality

### WebARXaaS

#### Short presentation

As a stretch goal, the employer wished for a way to quickly access the ARX functionality, taking advantage of the flexible REST API   provided by the ARXaaS service. It was therefore decided to implement an interactive web frontend. So the user can analyze or anonymize their data. Without the need for the user to install software on their local machine.

#### Technologies

The interactive Web service is implemented in React using multiple third-party frameworks in order to provide the best possible service

| Package     | Use                                                                                                                   |
| ------------| --------------------------------------------------------------------------------------------------------------------- |
| React       | React is a library for building interactive web user interfaces. It simplifies rendering content on the website and lets us split our code into many single-purpose components. |
| BootStrap 4 | Open source toolkit for making flexible interfaces adaptable for a wide range of screen sizes including mobile phones. And gives the website a professional looking color scheme. |
| Papa Parse  | Powerful tool for parsing and building CSV files with JavaScript                                                      |

#### Functionality

All the functionality can be accessed through a single page application.
Where the two main functionalities is *analyzation* and *anonymization*.

##### DataImport

The dataImport step is mandatory wherever the user wish to analyze or anonymize the data.
To load data the user clicks the load button, and selects a file.
Once the file is loaded, there will automatically be generated a section displaying each of the attribute headers from the file below.

##### Analyzation

The analyzation feature requires that the user already has loaded a *CSV* file, and set the correct *attribute types*.
By pressing the *Analyze* button, the website will make a call to the backend service on `/api/analyzation` containing a JSON formatted payload containing all the loaded data together with metadata.
Once the response back from the service is received it will be rendered multiple tables bellow containing metrics describing the analyzation quality.

| Metric table          | Content                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------- |
| Reidentification risk | Contains percentage likelihood on various *re-identification risks*                                 |
| Risk interval         | Gives metrics on how large portions of the entries in the data which is affected by each risk range |

#### Anonymization
The anonymization feature requires that the user already loaded a *CSV* file, set the correct *attribute types*, and uploaded a *CSV* file containing a generalization hierarchy for each of the *quasi-identifying* attributes.


### Operations

### Future developments

### Conclusion
