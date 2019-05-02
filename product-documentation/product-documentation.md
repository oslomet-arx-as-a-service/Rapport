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

As a stretch goal the employer wished for a way to quickly access the ARX functionality, taking advantage of the flexible REST API   provided by the ARXaaS service. It was therefore decided to implement an interactive web frontend. So the user can analyze or anonymize their data. Without the need for the user to install software on their local machine.

#### Technologies

The interactive Web service is implemented in React using multiple third party frameworks in order to provide the best possible service

| Package     | Use                                                                                                                   |
| ------------| --------------------------------------------------------------------------------------------------------------------- |
| React       | React is a library for building interactive web user interfaces. It simplifies rendering content on the website and lets us split our code into many single purpose components. |
| BootStrap 4 | Open source toolkit for making flexible interfaces adaptable for a wide range of screen sizes including mobile phones. And gives the website a professional looking color scheme. |
| Papa Parse  | Powerful tool for parsing and building CSV files with javaScript                                                      |

#### Functionality

All the functionality can be accessed through a single page application.
Where the two main functionality's is *analyzation* and *anonymization*.

##### DataImport

The dataImport step is mandatory wherever the user wishes to analyze or anonymize the data.
The user clicks load file and select the file they wishes to upload.
Once the file is loaded, there will automatically be generated a section displaying each of the attribute headers from the file bellow.

##### Analyzation

The analyzation feature requires that the user already has loaded a csv file, and set the correct *attribute types*.
Analyzation is started by pressing the *Analyzation* button.
By pressing the button the website will make a call to the backend service on `/api/analyzation` containing a JSON formatted payload containing all the loaded data together with metadata.
Once the response back from the service is received it will be rendered multiple tables bellow containing metrics describing the analyzation quality.

| Metric table          | Content                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------- |
| Reidentification risk | Contains percentage likelihood on various *re-identification risks*                                 |
| Risk interval         | Gives metrics on how large portions of the entries in the data which is affected by each risk range |

#### Anonymization


### Operations

### Future developments

### Conclusion
