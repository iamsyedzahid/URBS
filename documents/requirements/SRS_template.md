


Software Requirement Specifications

[Project Title]

Version: [xx.xx]

Project Code	
Supervisor	
Co Supervisor	
	
Project Team	






Submission Date	




 
 
[Instructions]
-	No section of template should be deleted. You can write ‘Not applicable’ if a section is not applicable to your project. But all sections must exist in the final document.
-	All comments/examples mentioned in square brackets ([]) are in the template for explanation purposes and must be replaced / removed in final document. 
-	This’ Instruction’ section should also be removed in final document.
-	MS-Word Reviewing feature must be used to get the document reviewed by supervisors or co-supervisors.


 
Document History
[Revision history will be maintained to keep a track of changes done by anyone in the document.]
Version	Name of Person	Date	Description of change
			[e.g. Document Created]
			[Added Non-functional requirements]
			[Added UseCase x.x.xx]
			
			
			
			

 
Distribution List
[Following table will contain list of people whom the document will be distributed after every sign-off]

Name	Role
	Supervisor
	Co- Supervisor
	


	
 
Document Sign-Off
[Following table will contain sign-off details of document. Once the document is prepared and revised, this should be signed-off by the sign-off authority. 
Any subsequent changes in the document after the first sign-off should again get a formal sign-off by the authorities.]

Version	Sign-off Authority	Sign-off Date
		
		
		
		
		
		
		


 
Table of Contents

1.	INTRODUCTION	7
1.1.	Purpose of Document	7
1.2.	Intended Audience	7
1.3 	Abbreviations ………………………………………………………………………………………...7
1.4.	Document Convention	7
2.	OVERALL SYSTEM DESCRIPTION	8
2.1.	Project Background	8
2.2.	Project Scope	8
2.3.	Not In Scope	8
2.4.	Project Objectives	8
2.5.	Stakeholders	8
2.6.	Operating Environment	8
2.7.	System Constraints	8
2.8.	Assumptions & Dependencies	8
3.	EXTERNAL INTERFACE REQUIREMENTS	9
3.1.	Hardware Interfaces	9
3.2.	Software Interfaces	9
3.3.	Communications Interfaces	9
4.	FUNCTIONAL REQUIREMENTS	10
4.1.	FUNCTIONAL HIERARCHY	10
4.2.	Use Cases	10
4.2.1.	[Title of use case]	10
5.	NON-FUNCTIONAL REQUIREMENTS	11
5.1.	Performance Requirements	11
5.2.	Safety Requirements	11
5.3.	Security Requirements	11
5.4.	User Documentation	11
6.	REFERENCES	12
7.	APPENDICES	13

  
1.	Introduction

1.1.	Purpose of Document 
[Describe the purpose of this document.]
1.2.	Intended Audience
[Describe people who are concerned with or are expected to use this document.]
1.3 	      Abbreviations	
[Describe the abbreviations use this document.]
1.4	           Document Convention
[Describe the font and font size that this document will be using]
 
2.	Overall System Description
2.1.	Project Background
[This section will establish business context in which system is being built. This will describe background information and will mention the actual problem / opportunity in business that triggered the project.]
2.2.	Project Scope
[This section will give an overview of project scope. This of project and will mention project boundaries and main functionalities that will be addressed in the system.]
2.3.	Not In Scope
[This section will highlight/explicitly mention the functionalities (if any) that are not in the scope of current project.] 
2.4.	Project Objectives
[This section will describe the objectives of project that how it is going to address the problem\opportunity identified in business environment and what would be the end result of project.]
2.5.	Stakeholders
[This section will describe stakeholders of the system. This will include different business user classes that are expected to interact with system and similarly the technical people who are going to be involved in software development/management]
2.6.	Operating Environment
[Describe the environment in which the software will operate, including the hardware platform, operating system, network environment and other software components or applications with which it must coexist.]
2.7.	System Constraints
[Describe the constraints imposed on the system by the external environment. External environment may be caused by the stakeholders, business conditions, technical issues, academic requirements etc and may include the following:
•	Software constraints
•	Hardware constraints
•	Cultural constraints (includes language etc.)
•	Legal constraints
•	Environmental constraints (e.g., the environment where the software will be installed, It could be a noisy environment, which may require that there is no sound event in the project).
•	User constraints (e.g., the project is developed for children, so it may be required that the project has more graphic controls rather than textual controls).
•	Off the shelf components that might be used in the project may have their constraints that are consequently transferred to the project.]
2.8.	Assumptions & Dependencies
[This section will identify: 
•	Any assumptions taken regarding the system or environment
•	Any dependency of system on any external factor.]
 
 
3.	External Interface Requirements
[This section is intended to specify any requirements that ensure that the new system will connect properly to external components. Place a context diagram showing the external interfaces at a high level of abstraction.]
3.1.	Hardware Interfaces
[Describe the characteristics of each interface between the software and hardware components of the system. This description might include the supported device types, the nature of the data and control interactions between the software and the hardware.]
3.2.	Software Interfaces
[Describe the connections between this system and other external software components (identified by name and version), including databases, operating systems, tools, libraries, and integrated commercial components. Identify and describe the purpose of the data items or messages exchanged among the software components. Describe the services needed and the nature of the inter-component communications. Identify data that will be shared across software components. ]
3.3.	Communications Interfaces
[Describe the requirements associated with any communication functions the system will use, including e-mail, web browser, network communications standards or protocols, electronic forms, and so on. Define any pertinent message formatting. Specify communication security or encryption issues, data transfer rates, and synchronization mechanisms.]
 
4.	Functional Requirements
4.1.	Functional Hierarchy
[This section will give a big picture of overall system functionality. The main modules/features of system and their sub-functions will be described here in the form of a functional hierarchy so that, before getting into the use case, audience could grab the idea of overall system functions.]
4.2.	Use Cases
4.2.1.	[Title of use case]
[Use Case Diagram]
[Use Case Description]

<Use case Id:  name>
Use case Id:	Write use case reference number.
Actors:	         <List of actors (external agents), indicating who initiated the use case>
Feature:                             <Feature from which the use case is driven>
Pre-condition:	<List the assumptions required before this Use Case can be executed. >
Scenarios
Step#	Action	Software Reaction
1.	Numbered actions of the actors	Numbered description of system responses
2.		
		
Alternate Scenarios: Write additional, optional, branching or iterative steps. Refer to specific action number to ensure understandability.
1a:
 
2a:

Post Conditions 
Step#	Description
	Sequentially list conditions expected at the completion of the use case.
	
 	
Use Case Cross referenced	<Related use cases, which use or are used by this use case>

 
5.	Non-functional Requirements
5.1.	Performance Requirements
[The performance characteristics of the system that are required by the business should be outlined in this section. Performance characteristics include the speed, precision, concurrency, capacity, safety, and reliability of the software. These characteristics define the performance of the project.]
5.2.	Safety Requirements
[Specify the requirements that are concerned with possible loss, damage, or harm that could result from the use of the system. Define any safeguards or actions that must be taken, as well as potentially dangerous actions that must be prevented. Identify any safety certifications, policies, or regulations to which the system must conform.] 
5.3.	Security Requirements
[Specify any requirements regarding security, integrity, or privacy issues that affect the use of the system and protection of the data used or created by the system. Define all user authentication or authorization requirements, if any. Identify any security or privacy policies or certifications the system must satisfy.] 
5.4.	User Documentation
[List the user documentation components that will be delivered along with the software, such as user manuals, online help, context-sensitive help and tutorials.] 
 
6.	References
[This section should provide a complete list of all documents referenced at specific point in time. Each document should be identified by title, report number (if applicable), date, and publishing organization.  Specify the sources from which the references can be obtained. (This section is like the bibliography in a published book).]

 
7.	Appendices
[This section should include supporting detail that would be too distracting to include in the main body of the document.]
