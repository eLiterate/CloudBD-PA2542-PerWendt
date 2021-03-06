
# The Cloud at Your Service #
## Chapter 2: Understanding Cloud Classifications
Chapter 2 covers
* Necessary technological underpinnings common to all cloud types
* Classyfing the types of clouds and their capabilities
* Chosing appropriate type of cloud

## The technical underpinnings of cloud computing ##
* a cloud needs servers on a network, and they need a home: aka #Data center#
* a cloud's servers needs to be virtualized. Otherwise not effective and too expensive
* a cloud needs an access API.
* a cloud needs some storage
* cloud applications need a database
* a cloud needs elaticity as a way to expand and contract application: Dynamicallay scalable

### Achieving high economies of scale with cloud data centers ###
car analogy: Data centrers equals the motor

### Ensuring high server utilization in the cloud with virtualization ###
car analogy: virtualization equals the suspension smoths out variations between applications that baerly needs CPU time and those that are compute intense

#Benefits of virtualization:#
* Decouples users from impolementation
* Decreases server provisioning from months to minutes
* Breaks software pricing and licensing

### Controlling remote servers with a cloud API
Car analogy: The Dashboard from with you monitors and controls it

Amazons API protected with X.509 keys

#Basic Amazon terms and operations#
* AMI: Amazon Machine Image: encrypted and signed machine image suitable to be run in an virtual server environment.
* Instance: The result of launcing an AMI is called an instance of that AMI
* Standard flow:
  1) Use standard a AMI by custumizing an existing one
  2) Bundle the AMI and get an AMI ID, to be able to launch as many instances of that AMI as needed
  3) Launch one or more instances
  4) Administer and use running instances
* Connecting

### Saving persistent data in cloud storage
car analogy: The trunk in which you store your luggage

AMAzon S3 terminology
* Object: Entity stored in S3
* Bucket: Container in S3 for data storage. Buckets are global
* Key: Unique identifier of an object in a bucket. Bucket name plus key uniquely identifies an object within all buckets
* Usage: 
  1) Create bucket in which to store your data
  2) Upload (write) data (objects) into the bucket
  3) Download (read) the data stored in the bucket
  4) Delete some data stored in the bucket.
  5) List the objects stored in a bucket

### Storing your application's structured data in a cloud database
Car analogy: The navigation system (???)

Relational database - SQL database
(RDMS -> Relational Database management system)
RDMS don't scale well

NoSQL movement
Non-relational data stores that break some of the fundamental guarantees of SQL in favor of being able to reach massive scale.
* Key value databases are item-orientated, meaning that all data relating to an item are stored in that item. A table can contain vastly different items. For example, a table can contain car makes, car models, car color items.

* NoSQL systems often provide weak consistency guarantees, such as eventual consistency and transactions restricted to single data items. You can impose full ACID (Atomicity, Consistency, Isolation, Durability) by adding a supllementary middleware layer.

* Several NoSQL systems employ a distributed architecture. In this way, the system can be scalued up easily by adding more servers, and failure of a server can be tolerated.

* SOme NoSQL advocates promote simple interfaces, such as associative arraus of key-value pairs. Other systems, such as native XML databases, promote support of the XQuery standard.

**_We are in the early days of cloud evolution, with a lot of development to be done!_**

Converting an existing application to use a cloud-based database (AWS SimpleDB or Google BigTable) is somewhere between difficult and not worth the trouble.

**Cloud database drawbacks:**

| Database use | Challenges |
| ------------ | ---------- |
| Transactional support and referential integrity   | The applications using cloud databases are responsible for maintaining the integrity of the transactions and relationships between tables.   |
| Complex Data Access   | Cloud databases excel at single-row transactions. But most non-trivial applications have to perform joins and other operations that cloud databases can't   |
| Business Intelligence | Application data has value not only in terms of powering applications but also as information that drives usiness intelligence. The dilemma of the pre-relational database, in which valuable business data was locked inside impenetrable application data stores, isn't something to which the business will willingly return. |

Cloud databases could displace relational databases for a significant segment of next-generation, cloud-enabled applications. But business is unlikely to be enthusiastic about an architecture that prevents application data from being used for business intelligence and decision-support purposes, which fundamentally requires a releational database. AN architecture that delivered the scalability and other advantages of cloud databases without sacrifycing information management would fit the bill. 

### Elasticy: Scaling your applciation as demand rises and falls ###
Elasticity enables an application running in the cloud to smoothly to expand and contract according to demand.

## Understanding the different classifications of clouds ##

### Amazon EC2 - Infrastrucure-as-a-Service ###
Amazon EC2 was the first and is by far the biggest. 
EC2 is the most general purpose, but has the least support for scaling. 
The LAMP stack is the easiest and most common EC2 configuration. 

EC2 uses Xen hypervisor, taking advantage of paravirtualization. Paravirtualized is more efficient than a virtualized environment.

### Microsoft Azure: Infrastrucure-as-a-Structure ###
Microsoft's Azure is IaaS in teh same way as Amazon EC2, but also has other services that operate more on a PaaS level.
The Windows Azure API is a REST-based api that uses x-509 client certifacates for authentification.

### Google App Engine: Platform-as-a-Service ###
App Engine is a pure PaaS cloud targeted exclusively at traditional web services, enforcing an application structure of clean separation between a stateless computation tier and a stateful sotrage tier.

Elasticity is not visible as in IaaS - automatic elasticity.

### Ruby on Rails in a cloud: Platform-as-a-Service ###
Ruby on Rails (RoR) is an Open-Source web application framework for the Ruby programming framework.

### Salesforce.com's Force.com: Platform-as-a-Service ###
Salesforce.com is the most sucessful SaaS application used in the enterprise.

### Private Clouds: Datacenter-as-a-Service ###
Private cloud (Internal cloud, corporate cloud) is a term for computing architecture that provides hosted services to a limited number of people behind a firewall.

More control than third-party-hosted services, such as AWS, Azure or App-Engine.

To have in mind when considering priivate clouds:
* Private clouds are small scale
* Legacy applications don't cloudify easily
* On-premises doesn't mean more secure
* Do what you do best

_#Amazon Virtual Private Cloud#_
Amazon VPC is a secure  and seamless bridge between a company's existing IT infrastructure and the AWS cloud. Not a private cloud as defined, but offers a hybrid model.
Amazon VPC enables an enterprise to connect its existing infrastructure  to a set of isolated AWS compute resources via a Virtual Private Network (VPN).

## Matching Cloud PRoviders to your needs ##
We will be applying a framework of decidion criteria by which you can evaluate the major cloud providers for your projects.

### Amazon web services IaaS Cloud ###
AWS is a flexible, low-level offering (closer to hardware) which means you have more psoosibilities. It will be high-performing at the cost of "everything is left up to you", including how and when to scale, move or replicate your data, and more.

*Use AWS when you want to:*
* Want to use third-party open-source software
* Have existing code
* Want to transfer a web app to your own machine/servers later
* Port code to another language
* Want complete control
* Need to stress/load test an app (for example, load up to 1000 instances)

### Microsoft Windows Azure IaaS and PaaS cloud ###
Azure is intermediate between application frameworks, such as App Engine, and hardware virtual machines, such as EC2.

*Use Azure if you want to:*
* Already use the .NET and SQL Server portions of the Microsoft Stack.
* Have existing code developed to those Microsoft APIS
* Have teams that normally develop in Visual Studio using C#
* Want to blend development from desktop to cloud
* Have no issue with lock-in to Microsoft

As for lock-in, Windows Azure is not looking as bad as Google App Engine.

### Google App Engine PaaS cloud ###
Google App Engine is a tightly controlled environment. The environment only supports Java and Python, and no installation of any open-source software is possible.

*Use App Engine if you:*
* Have no pre-existng code
* Are building request-resposne web apps or mashups
* Consider Time-to-Market the most importing thing
* Aren't doing anything fancy (installing software)
* Aren't worried about lock-in to Google

App engine is high on the lock-in scale.

### Ruby on Rails PaaS cloud ###
Ruby is slightly more computationally expensive than other languages

*Use Ruby on Rails if you_*
* Are building request-response web apps with existing Ruby experience
* Consider time-to-market critical
* Aren't doing anything fancy (installing software)
* Don't care about lock-in

Lock-in isn't a big concern with RoR, as we've said, there are many choices of RoR vendors and probably more to come.

### Force.com PaaS cloud ###
Force.com is an extension of the SaaS Salesforce.com. Many companies have been using Salesforce for along time. 
*Use Force.com if you:*
* Are already a customer of salesforce.com's SaaS customers-resource-management product
* Have a requirment for a simple mashupstyle of web application
* Are willing to use Force.com's specialized programming language
* Don't care about lock-in

## Summary ##
Compared and contrasted cloud flavors

Technology is not main driver, economics is
