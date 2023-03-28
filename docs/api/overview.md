# API
API stands for **Application Programming Interface**. In the context of APIs, the word Application refers to any software with a distinct function. Interface can be thought of as a contract of service between two applications. This contract defines how the two communicate with each other using requests and responses.

## Databases

#### Postgres
PostgreSQL, also known as Postgres, is a free and open-source relational database management system emphasizing extensibility and SQL compliance.

#### MySQL
MySQL is an open-source relational database management system (RDBMS).

#### MongoDB
MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas.

#### CouchDB
Apache CouchDB is an open-source document-oriented NoSQL database, implemented in Erlang. CouchDB uses multiple formats and protocols to store, transfer, and process its data. It uses JSON to store data, JavaScript as its query language using MapReduce, and HTTP for an API.

#### Neo4j
Neo4j is a graph database management system

## Query Languages

#### sql
Structured Query Language (SQL) is a standardized programming language that is used to manage relational databases and perform various operations on the data in them.

#### pl/pgsql
PL/pgSQL procedural language adds many procedural elements, e.g., control structures, loops, and complex computations, to extend standard SQL.

#### GraphQL
GraphQL was developed to cope with the need for more flexibility and efficiency! It solves many of the shortcomings and inefficiencies that developers experience when interacting with REST APIs.

#### MQL
MongoDB uses the MongoDB Query Language (MQL), designed for easy use by developers. The documentation compares MQL and SQL syntax for common database operations.

## In-Memory Datastores

#### Redis
Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker.

#### Memcached
Memcached is an in-memory key-value store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering ...

## Stream Processors

#### Kafka
Apache Kafka is primarily used to build real-time streaming data pipelines and applications that adapt to the data streams. It combines messaging, storage, and stream processing to allow storage and analysis of both historical and real-time data.

Producer
: Sends events to a broker on a specific topic

Broker
: The system in charge of storing events

Consumer
: Reads the events

Topic
: A category of events

Events
: Data that producers want to communicate to consumers

<div style="padding-left: 35px">
    <h5>Zookeeper</h5>
    Zookeeper is a centralized service essential for Kafka; it sends notifications in case of changes such as the creation of a new <strong>topic</strong>, crash of a <strong>broker</strong>, removal of a broker, deletion of topics, and so on.
</div>

#### RabbitMQ
RabbitMQ is a messaging broker - an intermediary for messaging. It gives your applications a common platform to send and receive messages, and your messages a safe place to live until received.

#### AWS Kenisis
Amazon Kinesis makes it easy to collect, process, and analyze real-time, streaming data so you can get timely insights and react quickly to new information.

## Specifications

[JSON API](https://jsonapi.org/format/)
: A specification for building APIs in JSON

[FHIR](https://www.hl7.org/fhir/http.html)
: FHIR is described as a 'RESTful' specification based on common industry level use of the term REST.
