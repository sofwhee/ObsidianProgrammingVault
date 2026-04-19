AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources.

Identity and access management is the framework and processes organizations use to manage and secure digital identities and control user access to critical information. Systems include user registration, identity authentication, role-based access control, and compliance auditing and reporting.

Identity and access management systems protect [sensitive data](https://www.sailpoint.com/identity-library/sensitive-data/) and systems from [unauthorized access](https://www.sailpoint.com/identity-library/unauthorized-access/) and [breaches](https://www.sailpoint.com/identity-library/security-breach/) while also streamlining and automating the management of users’ digital identities, access permissions, and security policies.

**IAM performs the following fundamental security actions:**

- Identifies individuals in a system through [identity management and authentication](https://www.techtarget.com/searchsecurity/answer/Authentication-vs-digital-identity-Whats-the-difference).
- Identifies roles in a system and how roles are assigned to individuals.
- Adds, removes and updates individuals and their roles in a system.
- Assigns levels of access to individuals or groups of individuals.
- Protects sensitive data within the system and secures the system itself.
### Identity management vs access management

The terms identity management and access management are often erroneously used interchangeably. The function of identity management is to confirm that an entity is who or what they are presented to be. In contrast, [access management](https://www.sailpoint.com/identity-library/access-management/) uses validated identity information to determine what resources an entity can use and how.

### Identity and access management vs identity management

Identity and access management and identity management are related but distinct areas within the broader scope of [cybersecurity](https://www.sailpoint.com/identity-library/cybersecurity/). Identity management is primarily concerned with managing identities, while identity and access management adds access control measures to ensure secure and appropriate access to resources.
### Identities
- Date of birth
- Domain
- Email address
- IP (internet protocol) address
- Medical history
- Online search activities (e.g., browsing history, electronic transactions)
- Purchasing history or behavior
- Social Security Number
- Username and password
### Digital resources 
include any assets that exist in digital form and can be accessed electronically.

- **APIs** (application programming interfaces)
	- a set of rules and protocols used to build or interact with software applications by allowing different software programs to communicate with each other
- **Cloud services**
	- services that deliver computing power, storage, and applications over the internet
- **Databases**
	- structured collections of data, such as SQL databases, NoSQL databases, and cloud-based data warehouses
- **Digital** **certificates**
	- SSL (secure sockets layer) /TLS (transport layer security) certificates and other forms of digital authentication used to secure communications and transactions
- **Digital** **content**
	- images, videos, audio files, animations, and interactive media
- **Email** **and** **communication** **platforms**
	- digital communication tools, such as email services, instant messaging apps, and social media
- **Files** **and** **documents**
	- text files, spreadsheets, presentations, PDFs (portable document formats), and other document types stored on computers or cloud storage services
- **IoT** (internet of things) devices
	- internet-connected devices that gather and transmit data
- **Network** **resources**
	- IP addresses, DNS (domain name system) records, routers, firewalls, and other network infrastructure components
- **Software** **applications**
	- cloud-based applications, mobile applications, desktop software, and enterprise systems
- **Virtual** **machines** **and** **cloud** **instances**
	- virtualized computing environments hosted on physical servers or cloud infrastructures
- **Web** **pages** **and** **websites**
	- any HTML (Hyper Text Markup Language) document accessible via a web browser, including informational sites, e-commerce platforms, and corporate blogs

### Access management

# Basic components of IAM

IAM products offer access control, which lets system administrators regulate access to systems or networks based on the roles of individual users within the enterprise.

In this context, _access_ is the ability of an individual user to perform a specific task, such as view, create or modify a file. Roles are defined according to job, authority and responsibility. [Key types of access control](https://www.techtarget.com/searchsecurity/tip/Types-of-access-control) include the following:

- Role-based access control.
- Discretionary access control.
- Attribute-based access control.
- Mandatory access control.

To gain access to those authorized resources, users must prove they are who they say they are. This is a complicated but necessary component of IAM, typically involving passwords, [challenge-response authentication](https://www.techtarget.com/searchsecurity/definition/challenge-response-system) and related methods.

### Authentication vs Authorization

Authentication is when an identity proves it is what/who it says it is. Authorisation, on the other hand, is proving that you have the permissions to access a resource.

**You need to be both authenticated and authorised in order to board a flight.** 

- Authentication is done with your passport or ID, where it is checked to ensure that the photo in your passport matches your face. This proves that you are who you say you are.

- After you have been authenticated, you need to prove that you have the permission to take a specific flight. This is done with your boarding pass

#### IAM Users / Groups / Roles

Authentication. That is, proving that you are who you say you are. They are like passports that get you through security in an airport.

#### IAM Policy

Without a boarding pass however, you cannot board a plane. The IAM policy is like a boarding pass, in that it grants or denies access to specific resources.

### One role at a time

Multiple policies can be attached to a single IAM role.

But an EC2 instance, or any AWS principal, service, or resource, can only assume one role at a time.