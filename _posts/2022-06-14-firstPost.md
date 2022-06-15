---
published: true
---
# Migrating from RDBMS to MongoDB

Hello friends! Before I get on with converting an old project that ran using **MariaDB** to **MongoDB** its imperative that I talk about MongoDB in this post, so here we go!

<p  >
	<h2 align="center"> Introducing NoSQL MongoDB!</h2>
</p>

After learning and implementing to use an SQL database in my previous semesters, I have always wondered about ‘NoSQL’ databases. Databases like _Cassandra_, _Neo4j_, _MongoDB_ are _NoSQL!_ Does it mean they don’t use SQL?
<div align="justify">
I personally don’t think that it’s the best way to reference a database. NoSQL doesn’t mean ‘No’SQL but rather ‘<strong>N</strong>ot ‘<strong>O</strong>nly’ ‘<strong>SQL</strong> All these databases I have mentioned above use SQL. These DB’s are also sometime referred to as a ‘Non-Relational Database’ and again I think that’s not a good way to reference it because for example in MongoDB you can store relational data except its stored differently compared to in a RDBMS.  Unlike <i>Cassandra</i> and <i>Neo4J</i> that are Column-based and Graph-based, MongoDB is a document-based database. It’s written in C++ and supports many APIs like JavaScript, Python, Ruby, Perl, Java etc. Now that my final project is using MERN stack for development, I have taken up the mantle to learn and deploy our database using MongoDB.</div>

<pre><a href="https://www.simplilearn.com/ice9/free_resources_article_thumb/What_is_MongoDB.PNG"> <img align="left" width="320" height="300" src="https://i.imgur.com/Skf7asI.png"></a>
</pre> <div align="justify"> &nbsp;When MongoDB first came out in 2009, it was exceedingly &nbsp;&nbsp;popular with many web developers because of its ease of &nbsp;&nbsp;use. It allowed web developers to work with data in the  &nbsp;&nbsp;same  format that they were using in their applications i.e., &nbsp;&nbsp; &nbsp;documents! But not only that, developers could work with  &nbsp;&nbsp;their data seamlessly while writing code because of Mongo &nbsp;DB's native drivers that make data appear like native &nbsp;&nbsp;objects in the programming language that is being used.</div>
&nbsp;&nbsp;&nbsp;&nbsp;
<div align="justify">
RDBMS have been around for decades and as you know they have a structure for storing data and require predefined schemas. RDBMS are strict, meaning that our field types must be defined ahead of time like whether a field will be an integer a string or other data type.  You don’t do that with Mongo. Data in MongoDB is stored in <strong>BSON</strong> under the hood but is represented as <strong>JSON</strong>, which is fundamentally different from an RDBMS. If you know JavaScript, then you'll be familiar with the JSON format.</div>


Sample JSON document I inserted into one of my favorite movies “Bullitt” collections called “BullittCast”

```json
db.BullittCast.insertOne( [
{
	"Id": 3,
	"Fname": "Steve",
	"Lname": "McQueen",
	"Email": "steve_mcqueen@gmail.com",
	"Address": {
	"Street": "29 Oakmont Dr",
	"City": "Los Angeles",
	"State": "CA",
	"Zip_Code": "90049"
},
	"PhoneNumbers": [
		{ "type": "home", "number": "310*******" },
		{ "type": "mobile", "number": "310*******" }
		]
} ] ) 
```
<div align="justify"> 
MongoDB requires less management and has simpler data models, unlike an RDBMS which requires a highly trained expert to monitor the database. While learning Oracle in my previous semesters I used to get annoyed with constraints of data volumes and capacity limitations so I’m hoping that the NoSQL database would allow me to avoid those issues and cut the drama that follows. I have also read that RDBMS scales up! What that means is bigger load, bigger server whereas NoSQL scale-out. They distribute data across multiple hosts seamlessly. No wonder many organizations with large volumes of data are thinking of migrating from RDBMS to a NoSQL database </div>
<br>
<div align="justify"> 
MongoDB databases are flexible, by that I mean by default there is no schema in place or let’s say they have a dynamic schema (no DLL). You can store any type of data in any document, and this is by design.  If you ever need a schema to add more structure, it can be added at any time. MongoDB offers plenty of useful features (Ad-hoc queries, aggregation, capped collection, file storage, indexing, load balancing, replication, server-side JavaScript execution) that make it a user-friendly database.[1] </div>
<br>
<div align="justify">
MongoDB database scale very easily and is super-fast to query data. It provides easy and fast integration of data (no ERD required!!). Since data is stored together when your application is fetching data, it doesn't need to reach out to let’s say collection A, merge it with collection B, and then with collection C. Instead, it goes to collection A and with its efficient querying mechanism running behind the scenes, it can go through all the data very fast when looking for a specific document and when it finds that document, jobs done. It doesn't need to do any merging most of the time. So, this is really where the speed, the performance and flexibility come from. They say in comparison to an RDBMS it can do these operations over <strong>1500 times faster!!!</strong></div>
<br>
<div align="justify"> 
You have the option to host the MongoDB server on your local machine but will have to manage the server upgrades. Instead, you can use it directly from the open-source community server as MongoDB offers a could platform called MongoDB Atlas and takes all the hassle of hosting on your own. MongoDB Atlas provides a free tier cluster which gives the account holder 512MB storage space for free, forever! This is a great opportunity to avail yourself if you are considering hosting your project database. They also provide an opportunity to load a sample database in this free account. I have set up my capstone project database on the Atlas cloud and this sample database came in handy during the learning process. </div>
<br>
<div align="justify"> 
You can go through many videos online on how to get started with MongoDB, I mean creating a cluster on MongoDB Atlas, hosting on AWS space, loading sample collections and how start your own Database. I’m not going to dwell on all those details here, but I must talk about MongoDB compass and Mongo Shell.</div>
<br>
<div align="justify"> 
MongoDB offers an excellent GUI software that you can download and connect to your localhost (data on your machine) or if you have a MongoDB instance on the cloud (data in Atlas Cluster) you can go there and get a link to connect via the compass. On compass click on New Connection and copy-paste the link in the provided box and click <i>CONNECT!</i>  Make sure you have the correct username and password in the link, and you are linking the correct database that you created. See my connection below </div>

<p align="center"> <img width="500" height="300" src="https://i.imgur.com/KMkgKIy.jpg">  
  

<div align="justify"> 
Using the compass, you can pretty much do everything like creating a database, creating collections, documents, JSON fields (Key-Value Pairs). You can update and delete and basically enjoy the dynamic representation of your cluster. Watch my set up video presentation to take a deeper look at the compass GUI tool. When processing large amounts of data, MongoDB Shell's speed can suffer. Furthermore, the MongoDB Shell operates independently on the database, preventing users from independently analyzing and viewing data changes. Users using MongoDB Compass, on the other hand, may visualize their database and its changes without having to worry about performance.</div>

For those who have worked with SQL will be able to understand this table below

 
|SQL                         |MongoDB                       |
|-------------------------------|-----------------------------|
|`Table`            |`Collection`         |
|`Row`            |`Document`            |
|`Column`|`Field`|
|`Index`|`index`|
|`Joins`|`Embedded documents & linking`|
|`Where`|`$match`|
|`Group by`|`$group`|
|`Count()`|`$sum`|
|`Order by`|`$sort`|
  

<div align="justify">
MongoDB database holds multiple collections, and each collection can then hold multiple documents,
this is how MongoDB structures its data. Databases and collections are created only when a document is inserted, only when you need a specific database or collection. A document can't directly be inserted into a database, it's always part of a collection, so keep that layered architecture in mind when you create your DB. Documents have a certain structure i.e... each document needs a unique ID which must be called _id, MongoDB creates this by default, or you can set this on your own. Then you can have embedded documents as well as arrays, texts, numbers, and all other data types that you mostly know if you have experience working with SQL.
 </div>
 <br>
 <div align="justify">
 An important part or aspect of working with a database is that you can perform <strong>CRUD</strong> operations. CRUD stands for <strong>Create</strong>, <strong>Read</strong>, <strong>Update</strong> and <strong>Delete</strong>. MongoDB offers multiple crud operations for a single document and bulk actions; you can insert one element or one document or many documents and you can find many documents or find one document. Some methods require arguments, ‘insertOne ()’ for example needs to know what you want to insert, other methods like find can use arguments as you will see in my video below.
 </div>
 <br>
<div align="justify">
<strong>‘find()’</strong> by the way also returns a cursor, not a list of documents. That cursor is useful for manually going through the documents. Imagine if you have hundreds and thousands of documents which would have to be transferred over the wire in one go!! That would be a heavy load on your bandwidth. You can use filters on find and on update and delete to narrow down the documents you want to find, update, or delete.</div>
<br>
Syntax: db.collection.find( <query>, <projection> ).cursor modified
  		//Provides functionality similar to the SELECT command in SQL
```json
	<query> - WHERE condition,
	<projection> - fields in result set

//Example: 
	const qytCursor = db.Cars.find({qty: {$lt: 10}})
```
 <br>
<div align="justify">
Filters and operators allow you to narrow down the set of data. We can use filters and operators to retrieve data from a collection.  As per the example above, you can see that I used the less than operator (<i>lt</i>) Now, these are special comparison operators provided by MongoDB. Some I know for sure are <i> ‘gt’</i> for Greater Than, <i>‘eq’</i> for Equal, <i>‘ne’</i> for Not Equal etc. You can find the syntax of all comparisons, logical, geospatial etc. on <a href="https://mongodb.com">mongoDB</a>. They start with a dollar sign ($), and this allows you to simply limit the amount of data you are fetching. You can also use projection to then take that data you fetched and tell MongoDB which fields you want to get and which you don't want to get. So, filters allow you to restrict the number of documents, projections then allow you to restrict the number of fields per document so to say. </div>
<br>

***Getting Started with MongoDB Atlas***

This [link](https://www.mongodb.com/basics/mongodb-atlas-tutorial#creating-a-mongodb-atlas-account) will take you to the literature on how to create an account with MongoDB or you can watch the first 6.30s of this [how to](https://www.youtube.com/watch?v=S4fi6Qux-4g) video to setup your account. 

Video below shows a quick tour on basic set up and my effort in trying to explain using some CRUD operations. I would be doing most of the work on the shell.

<div align="center" class="embed-responsive embed-responsive-16by9">
<iframe width="560" height="315" src="https://www.youtube.com/embed/7PhDXhcd-aA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
<br>
<div align="justify">
Now that you have a fair idea of setting up and getting started with MongoDB, be sure to look out for my next post where I will take you through the process of migrating one my 3rd semester web projects from MariaDB to MongoDB. See you on the other side. </div>
<br>

>***References:***

[1]		“Data Modeling w/ MongoDB,” _www.youtube.com_. https://www.youtube.com/watch?v=y0nx8LtcO4g&list=PL4RCxklHWZ9t2KI3XiRLbqsMKB_iXxScv&index=8 (accessed Jun. 15, 2022).

[image]		_Simplilearn.com_, 2022. https://www.simplilearn.com/ice9/free_resources_article_thumb/What_is_MongoDB.PNG (accessed Jun. 15, 2022).

