+++
title = 'MongoDB in Action 2笔记'
date = 2025-03-21T16:47:35-06:00
draft = false
+++

### Chapter 1

Perhaps the biggest reason developers use MongoDB isn't because of its scaling strategy, but because of its intuitive
data model. MongoDB stores its information in **documents** rather than rows.

A document-based data model can represent rich, hierarchical data structures. It's often possible to do without the 
multitable joins common to relational databases.

... the distinction between a **tabular** and **object** representation of data ...

The umbrella term **NoSQL** was coined in 2009 to lump together the many relational database gaining in popularity at the 
time, one of their commonalities being that they use a query language other than SQL.

The most important thing to remember from its history is that MongoDB was intended to be an extremely simple, yet
flexible, part of a web-application stack.

Internally, MongoDB stores documents in a format called Binary JSON, or **BSON**. 

BSON has a similar structure (of JSON) but is intended for storing many documents.

Where relational databases have tables, MongoDB has **collections**.

The data in a collection is stored to disk, and most queries require you to specify which collection you'd like to
target.

The technique of separating an object's data into multiple tables is known as **normalization**. A normalized data set,
among other things, ensures that each unit of data is represented in one place only.

But strict normalization isn't without its costs. Notably, some _assembly_ is required.

A document-oriented data model naturally represents data in an aggregate form, allowing you to work with an object
holistically.

MongoDB groups documents into collections, containers that don’t impose any sort of schema. In theory, each document in 
a collection can have a completely different structure; in practice, a collection’s document will be relatively uniform.

Your application code, and not the database, enforces the data's structure.

To say that a system supports **ad hoc queries** (即席查询) is to say that it isn’t necessary to define in advance what sorts of 
queries the system will accept. Relational databases have this property; they’ll faithfully execute any well-formed SQL 
query with any number of conditions.

One of MongoDB’s design goals is to **_preserve_** most of the query power that’s been so fundamental to the relational 
database world.

With MongoDB, you can create up to 64 indexes per collection.

MongoDB provides database replication via a topology known as a **replica set**.

Replica sets distribute data across two or more machines for redundancy and automate fail-over in the event of server 
and network outages.

Since MongoDB v2.0, **journaling** is enabled by default. With journaling, every write is flushed to the journal file every
100ms. If the server is ever shut down uncleanly (say, in a power outage), the journal will be used to ensure that 
MongoDB’s data files are restored to a consistent state when you restart the server. This is the safest way to run 
MongoDB.

MongoDB was designed to make horizontal scaling manageable. It does so via a range-based partitioning mechanism, known 
as **sharding**, which automatically manages the distribution of data across nodes. There’s also a hash- and tag-based 
sharding mechanism, but it’s just another form of the range-based sharding mechanism.

The core database server runs via an executable called `mongod`. The `mongod` server process receives commands over a 
network socket using a custom binary protocol.

The MongoDB command shell is a JavaScript-based tool for administering the database and manipulating data. The `mongosh` 
executable loads the shell and connects to a specified mongod process, or one running locally by default. 


### Chapter 2
MongoDB divides collections into separate databases. Unlike the usual overhead that databases produce in the SQL world, 
databases in MongoDB are just _namespaces_ to distinguish between collections.

Databases and collections are _created only_ when documents are first inserted.

Every MongoDB document requires an `_id`, and if one isn't present when the document is created, a special MongoDB
`ObjectID` will be generated and added to the document at that time.

You can set your own `_id` by setting it in the document you insert, the `ObjectID` is just MongoDB's default.

A **query selector** is a document that's used to match against all documents in the collection.

Note that calling the `find` method without any argument is equivalent to passing in an empty predicate; `db.user.find()` 
is the same as `db.users.find({})`.

Rather, the query itself is a document. The idea of representing commands as documents is used often in MongoDB and may
come as a surprise if you're used to relational databases.
