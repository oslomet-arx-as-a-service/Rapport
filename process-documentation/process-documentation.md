### Front page

### Preface

### ToC

### Introduction

This report contains the work done in this bachelor project that led to the final result. The project planning started 18.07.2018 and the bachelor project started 08.01.19 and lasted to 23.05.2019. The team has worked at Oslomet university in Oslo and NAV IT headquarters at sannergata 2 in Oslo. The team has worked together four days a week with fixed core work hour's nine to four. These days the team have worked together as a group, where they have worked on there assigned sprint tasks as well as made important project decisions. In addition to this all team members have worked from home as well.

In the course of the project period the team has had close contact with the product owner Robindra at NAV IT. In the first meeting with the product owner the minimal viable product was decided. The system should anonymize a tabular data set based on the user’s desired anonymity level with a minimum of K=4 anonymity. This functionality was to be delivered in a Phyton client. As a stretch goal the  product owner and the team wanted a WEB application.

This document starts with the teams planning and development methods......

### Planning and methods

This chapter will explain the creation of the team and planning of the project as well as the planning during the project. The chapter starts with development methods applied by the team. Followed by project phases and the project conclusion and documentation.

### Development methods



#### Agile work process: [https://agilemanifesto.org/]

The team decided to use a agile work process with our product owner's demands and wishes as our top priority. The team worked in to week sprints. At the start of every sprint the team did sprint planning and chose the user story's to add to the sprint backlog. The team then added the user storys chosen for the sprint to our Khanban board in Asana. The team members chose or assigned the different tasks as a group. A definition of done was specified for each sprint by the group. An example of this was every feature had to be tested before merging into the master branch. During the each sprint the team had daily scrum meetings to keep the rest of the team updated on each individuals progress as well as to share knowledge in the team. At the end of the sprint the team had a sprint retro meeting where each member made post-it notes labeled start, stop and continue. The start post-it notes where suggestions of items to be implemented in the next sprint. The stop post-it notes where things that had not worked well for the team or an individual. The continue post-it notes where items that worked well in the sprint and the team member wanted to keep doing in the next sprint. The project was divided in to seven sprints with a duration of two weeks where we presented the new features to our product owner at the end of each sprint. Then based of the feedback from the product owner the team created new user story's and definition of done for the next sprint.

#### Continues integration pipeline

The team decided early in the process to set up a CI pipeline to automate tests and deployment.
Every time a team member pushed a commit to our version control host Git . Travis testes every branch in a virtual environment before it can be allowed to be merged into master branch. If the job passes all test. It can be merged into to master branch providing it passes Code climate static code analyses test and SNYK vulnerability tests. After a team member approves the code review the branch is merged into master branch. Travis then deploys docker container to Google cloud and the NAV IT nais platform. Before deploying JAR and javadoc to Maven witch then hosts are Javadoc.

#### Test driven development

In the teams definition of done it required tests to be made and passed for all features. This had to be done before merging into master branch. This worked well for the team and we ended up with 90% plus test coverage.The team also used Linter in the team members IDEs to make sure the code was clean.

#### Code reviews

In the planning process the team decided to use Git as version control. After Travis,Code climate and SNYK test passed a team member had to review the pull request. A team member had to read and approve the code before a merge to master branch could be done.

#### Feature slicing

The team worked actively on slicing up big features requested by the product owner into smaller features. After slicing the features. The team evaluated the different features and decided with the product owner which features where best to implement first. This made sure that the product owner got features delivered fast. Deliverys where made in small increments that provided the most value as fast as possible.

### Project phases

#### Initiation

 The project started with a get to know meeting at Starbucks in Torgata 18.07.2018. Everyone discussed their expectations for the project and the way forward. Sondre had a contact person at NAV IT and had talked about a possible bachelor project with them. Our contact person at NAV IT had mentioned key words such as Kafka, docker / kubernetes, Java, Python,data lakes, data virtualization as possible things we can work with. During this meeting It was also suggested to recruit a fifth party to the group. The group then contacted Viktor and asked if he wanted to join the team. After a second get to know meeting Viktor joined the team. 
 
 #### Planning

 The team in Norway Sondre, André, Viktor and Jeremiah had a meeting with NAV IT while Julian was studying abroad. This information meeting was with Tommy and Gøran. In short, the goal was to build a "pipeline" from raw data that NAV sits on and make available to stakeholders outside NAV (media, private persons, etc.). The pipeline was to accommodate the entire range from integration with raw data systems at NAV, to visualization and typically front-end solutions. The product that NAV's Open Data project was to deliver is a common platform / toolbox for delivering open data to the Norwegian population. The idea was that the team will deliver a contribution to this project. The team must be involved in developing the plan for the specific product we are going to deliver, but it will be within the Open Data project framework. Concrete features in the Open Data project that the team could participate in was, API - backend pipeline , Portal - web platform (data.nav.no) and Meta-data system for for automatic generation of visualizations . The team was given some task to complete before january 1st 2019. Every team member had to read the Accelerate book. And the team also where asked to get to know Docker and Kubernetes. Further more the team was asked to brainstorm ideas for solving “How can NAV deliver specific data sets they are sitting with, in a good and user-friendly manner (user-friendly for developers, media houses, private persons)". A purposed idea was to focus on a specific data type and expand it eventually if the solution is good or if there was time to improve the solution. The initial idea was to focus on treatment time. What kind of issues take the longest time  and shed light on treatment time. The goal was to streamline assessment of departments time spent on treatment. At 18.10.18 the team had it's first meeting with Eva Hadler to talk about guidance for the bachelor project. Eva was highly recommended and the teams was happy she decided to be the supervisor for the project. Eva shared her experiences with undergraduate projects and what was expected. The team had a sync meeting 23.10.18 and got Julian up to date on what the team had done in Norway. After a couple of meetings discussing frame works and tools the group had there first bachelor meeting in 2019. The team decided on regular workdays and hours. The team decide on to work with Github, Asana, Travis and Slack.  At  this point the project task was still a bit in the air. At are next group meeting at NAV IT. Robindra and Paul  presented the data anonymity project to the team. The essence of the project was to make Arx's functionality available to NAV's systems and build a framework that makes Arx's anonymization functionality available to NAVs data scientist. The sought after functionality where, being able to submit data sets to the service and receive an anonymized data set of the desired anonymity level. The group discussed different approaches to the problem and tools we can use. Tentatively the team planned an overall architecture with Java / Spring backend and Python / Jupyter Notebooks, Javascript / React frontend and Docker as scalability. The group agreed that this was a good project with both enough content and room for stretch goals.  At the next meeting 01.01.19 at NAV IT Robindra gave the team an introduction to ARX. The team decided on a English working language for documentation and code to make the open source project available to everyone. Robindra got the title as product owner and Sondre got the title as Scrum master.

 #### Execution

The team used the first two weeks of the project to make the pre-project report and decide witch software tools, software languages, and working methods to be used in the project. After this the team got all computer updated to the same version of software before starting group education. The group used the Pluralsite [https://www.pluralsight.com/] Scrum course to get all members up to date on Scrum as well as to make sure the team had the same understanding of what Scrum is. The team had a solid Java programing base but need to learn more Phyton programming. Sondre had a Phyton programming course for the rest of the team to accelerate the Phyton programming skills of the group. The team decided to work in to week sprints. It was decided to use seven sprints for development of the application and for weeks to write the project report.
 
### Project conclusion and documentation
 

#### Planning tools


-Competence building

-Budget(Google cloud)

### Development process

#### Challenges met and choices made

#### Descriptions of the sprints

#### Development tools

#### Lessons learned during development

### Product specification

#### Main Specifications descriptions

Process

The development team will use the SCRUM framework to organize tasks, work, and project progress.

Functional demands

Backend
The system should anonymize the data based on the user’s desired anonymity level
The system should be able to evaluate the anonymisation level of a given data set
Frontend
The Python package should support standard visualisation of the results.

Non-Functional demands
Backend
Platform: Docker/Nais/Kubernetes
Runtime: Java/JVM
Framework: Spring

Frontend (Consumers)
Python package
Javascript (websites)

- Stretch goals descriptions

Javascript (website)

- Delivery

### Closing 

### Sources

https://agilemanifesto.org/
https://www.pluralsight.com/
