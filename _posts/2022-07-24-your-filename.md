---
published: false
---
# Migrating from RDBMS to MongoDB

Howdy!

In my previous post we talked about MongoDB’s growing popularity and its compatibility with other databases with regards to business intelligence and scalability. I also wrote about how documents in a collection need not be well defined or structured and demonstrated some CRUD operations using Mongo Shell through my video. 

> Let me take this topic further and talk about migrating from an RDBMS to NoSQL, especially MongoDB. 

Data partitioning and data replication are the major features that set NoSQL apart from conventional RDBMS. Despite these advantages, most big and medium-sized software systems currently in use are still RDBMS-based since the migration process is fraught with difficulties. The first is the amount of data that needs to be moved. Organizations typically decide to move their databases when the amount of data being stored is enormous and the RDBMS can no longer meet the demands for high availability and scalability. The way the relational database architecture avoids data redundancy, which is a feature of the NoSQL models, presents another obstacle.  

