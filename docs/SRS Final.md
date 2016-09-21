<div align=center>
   <h1><b>Software Requirements Specification</b></h1>
   <h1>Smart Search for Education</h1>
   <b> Web Application</b><br />
   <b> Version <i>1.0</i></b>
</div><br /><br /><br />


#### Team SSE

- **K Manoj Kumar**  U101114FCS
- **Vinit Koshti**  U101114FCS
- **Jagrit Kaushik**  U101114FCS
- **Jeel Shah**  U101114FCS172
- **Mansi Singh**  U101114FCS090

#### NIIT University - Software Engineering
##### 21-Sep-2016

<hr/><br />

# Table of contents
1. [Introduction](#introduction)  
1.1 [Purpose](#introduction-purpose)  
1.2 [Document Conventions](#introduction-document_conventions)  
1.3 [Intended Audience and Reading Suggestions](#introduction-intended_audience)   
1.4 [Product Scope](#introduction-product-scope)  
1.5 [References](#introduction-references)  
1.6 [Glossary](#introduction-terminology)
2. [Overall Description](#od)  
2.1 [Product Perspective](#od-pp)  
2.2 [Product Functions](#od-pf)  
2.3 [User Classes and Characteristics](#od-ucc)  
2.4 [Operating System](#od-os)  
2.5 [Design and Implementation Constraints](#od-di)  
3. [External Interface Requirements](#eir)  
3.1 [User Interfaces](#eir-ui)  
3.2 [Hardware Interfaces](#eir-hi)  
3.3 [Software Interfaces](#eir-si)  
3.4 [Communications Interfaces](#eir-ci)  
4. [System Features](#sf)  
5. [Other Nonfunctional Requirements](#onr)
6. [Other Requirements](#otherreq)  
[_Appendix_](#appendix)  
<hr />  


##### Product : Smart Search for Education (Web Application)
##### Description : An offline music recommendation system
##### Development Status  : Design

----

## Revision History

#### Latest
    Version : 1.0
    Status : Documentation and Design Specifications
    Date : 21-09-2016

# 1. Introduction to SSE <a name="introduction"></a>
## 1.1 Purpose <a name="introduction-purpose"></a>
The purpose of this document is to present a detailed description of the Smart Search for Education Web Application. It will explain the purpose and features of the system, the interfaces of the system, what the system will do, the constraints under which it must operate and how the system will react to external stimuli.
This document is intended for both the stakeholders and the developers of the system and will be proposed to the Professor of Software Engineering (CS 332) for approval.

## 1.2 Document Conventions <a name="introduction-document_conventions"></a>
- Terms in italics.
- Features and technical terms are displayed in bold.
- TBD means "To be Determined", these are the components that are not yet finalised.
- For more clarification visit [Terminology](#introduction-terminology).

## 1.3 Intended Audience and Reading Suggestions <a name="introduction-intended_audience"></a>
- This document is intended to anyone who has basic coding skills and knowledge in Software Development and Use Case Diagrams

- The document is divided into 5 phases where section 1 and 2 can be understood by anyone who has knowledge about software but section 3,4 and 5 are can be understood by Software Developers and Software Architects.

This Software Requirements Specification document includes the following sections:

- Overall description
- External Interface Requirements
- System Features
- Other Non Functional Requirements


## 1.4 Product Scope <a name="introduction-product-scope"></a>

- This webapp is intended to perform unstructured dynamic search on learning course materials useful for learners to easily locate the topics in loads of learning material uploaded. This software will be designed to maximise the productivity of learners by providing them most recommended search according to their request. The webapp will be very simple to understand and use, keeping the efficiency consistent.

- The webapp will be using OpenSource Optical Character Recognition Software **_Tesseract_** and Search algorithms from **_Elasticsearch_** to display the most recommended suggestion according to the search keywords given by the user. The interface will be very simple and easy to understand like the Google Search.

## 1.5 References <a name="introduction-references"></a>

- IEEE. IEEE Std 830-1998 IEEE Recommended Practice for Software Requirements Specifications. IEEE Computer Society, 1998.
- Tesseract-OCR - to extract text from images.
- ElasticSearch - Developed on Apache Lucene (Search).

## 1.6 Terminology <a name="introduction-terminology"></a>
| Term | Description |
| --- | --- |
| User | Any person who is interacting with the application is a _user_.|
| System | The package of all the components which takes input and gives output to demonstrate the features of the application is called System. |
| Database | Collection of information on different topics related to each other. |
| Library|  _library_.|
| Store | This is the persistence layer of whole system. |

# 2. Overall Description <a name="od"></a>

## 2.1 Product Perspective <a name="od-pp"></a>
This system is broadly classified into two products.

- **Optical Character Recognition**: for recognition of text from scanned images of documents and other articles.
- **ElasticSearch**: On the basis of keywords generated, displays the most relevant suggestions available in the database.

Using _Tesseract_ for Optical Character Recognition  text can be recognized from any kind of scanned images (jpeg/jpg/png) and extract it into a _.txt_ file.

_Elasticsearch_ is used for unstructured search which can search and analyze in real-time. It is based on sophisticated RESTful API.


#### System Use-Case Diagram
![system_use_case_diagram](https://cloud.githubusercontent.com/assets/14366356/18707511/0c63f0be-8014-11e6-81af-d88caea556fb.png)

## 2.2 Product Functions <a name="od-pf"></a>
SSE is a webapp where adminstrators will be uploading documents ( which may be in image format like scanned books, notes and other documents or other formats like .doc,.pdf ) which will be analysed and stored in the database.
The file will be completely searchable by the users.

When users search for a topic or concept, the most recommended suggestions will be made available to the the user from the database. The user will also be provided a download link to download the document. Users can also give their review for the document(upvote/downvote).

<b>_Admin_</b> can perform the following actions besides <b>_User_</b> actions:
- upload documents (.jpg/.jpeg/.png/.doc/.pdf)
- insert/delete/modify the document uploaded.

<b>_User_</b> can perform following actions:
- search for a concept or topic.
- After login into the system using user-id and password:
   - download or view the document.
   - review (upvote-downvote) the document.

## 2.3 User Classes and Characteristics <a name="od-ucc"></a>
- Any learner and researcher can use the Application. Any user can search for a specific concept or topic and thereby view or download the same.
- The users are mostly expected to be well connected to Internet for viewing or interacting with the application. 
Users also have a Add to Library option and they can share their libraies with other users.

## 2.4 Operating Environment <a name="od-os"></a>
- A Web Browser is mandatory to run the application(Supports Google Chrome/ Firefox/ Safari).
- Web Browser will access the application using the URL which may run on any kind of Operating System (Windows/Linux/Mac OS/Android/iOS).

## 2.5 Design and Implementation Constraints <a name="od-di"></a>
[_ElasticSearch_][elastic-search-website] has few constraints as follows:
- Change of number of shards - Since each index has 5 shards by default. Number of primary shards cannot be changed once the index is created. Replicas can be increased anytime.
- Partition Tolerance - Partitioned clusters can diverge unless discovery.zen.minimum_master_nodes set to at least N/2+1, where N is the size of the cluster. If configured correctly, the partition without a quorum will stop operating, while the other continues to work. See [this](http://elasticsearch-users.115913.n3.nabble.com/Split-brain-td3620149.html).

[_Tessearct-OCR_][tesseract-website] has few constraints as follows:
- Tesseract can only handle left-to-right languages. While you can get something out with a right-to-left language, the output file will be ordered as if the text were left-to-right. Top-to-bottom languages will currently be hopeless.
- Tesseract is unlikely to be able to handle connected scripts like Arabic. It will take some specialized algorithms to handle this case, and right now it doesn't have them.
- Tesseract is likely to be so slow with large character set languages (like Chinese) that it is probably not going to be useful. There also still need to be some code changes to accommodate languages with more than 256 characters.
- Any language that has different punctuation and numbers is going to be disadvantaged by some of the hard-coded algorithms that assume ASCII punctuation and digits.

## 2.6 User Documentation <a name="od-ud"></a>
- A well-defined user manual will be available which can be accessed by clicking on the "Help" Tab of the WebApp.
- User-Documentation will be available on [GitHub](https://github.com/kmanojkumar/Smart_Search/)

## 2.7 Assumptions and Dependencies <a name="od-ad"></a>
Opensource Softwares and Libraries used for the implementation are:
- [*_Elastic Search_*] [elastic-search-website]
- [*_Tesseract-OCR_*] [tesseract-website]
- [*_Bootstrap_*] [bootstrap-website]

# 3. External Interface Requirements <a name="eir"></a>

## 3.1 User Interfaces <a name="eir-ui"></a>
- A Web-based UI developed using BootStrap and other Front-End languages.
- The UI will be very simple to use with a Search box and user's personal libraries along with few recent documents displayed.

## 3.2 Hardware Interfaces <a name="eir-hi"></a>
None as of now, TBD.

## 3.3 Software Interfaces <a name="eir-si"></a>
- Web Browser - independent of operating systems.
- LAMP Stack.

## 3.4 Communication Interfaces <a name="eir-ci"></a>
- Internet Connection is used.
- FTP and HTTP Protocol.

# 4. System Features <a name="sf"></a>
System Use Case Diagram is as follows:
![system_use_case_diagram](https://cloud.githubusercontent.com/assets/14366356/18715046/6d5f0d06-8035-11e6-9a57-4078dcecb70e.png)

#### Use Case Description Table
| Use Case (ID) | Description |
| --- | --- |
|Suggest Doc (UC1)|User can suggest documents|
|Edit Profile (UC2)|Manage User Profile|
|Login (UC3)|Metadata will be saved after login|
|User ID (UC4)|User-ID of the User|
|Password (UC5)|Password of the User|
|Follow Library (UC6)|User can follow libraries|
|Search (UC7)|User gives search keywords|
|History (UC8)|Log of user search history|
|Upvote (UC9)|User can upvote a document|
|Add to Library (UC10)|User can add documents(books/notes) to personal libraries|
|Result (UC11)|Search results|
|Download Result (UC12)|Users can download documents|
|Insert (UC13)|Admin can insert new documents|
|Delete (UC14)|Admin can delete documents|
|Modify (UC15)|Admin can modify documents|
|Image (UC16)|Browse custom scanned images|
|View (UC17)|View documents|
|Document (UC18)|User can search within a document|
|Books (UC19)|User can search for books|
|Database (UC20)|System Database|

----
#### Functional Requirements
| **Identifier for Requirement** | **Functional Requirement Name** | **Description** |
| --- | --- | --- |








