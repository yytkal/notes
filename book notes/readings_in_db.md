---
cards-deck: tech::db
---
# TODO:

## What Goes Around Comes Around
https://people.cs.umass.edu/~yanlei/courses/CS691LL-f06/papers/SH05.pdf

## Architecture of a Database System
http://mperdikeas.github.io/architecture-of-a-database-system.pdf

# Ch1: Background
XML is piece of crap.
JSON is reasonable choice for sparse data.
Map-Reduce is not right architecture for broad scale. Turning into HDFS.
In data warehouse, column stores replaced row stores.
In OLTP, main-memory SQL engines with lightweight transaction management are becoming the norm.
Basic architecture: parsing/optimizer/executor.
Summary: Last decade, mostly reinvent wheel.

## Architecture of a Database System

### RDBMS

#### components
#card
client communication manager
process manager
relation query processor
transaction storage manager
shared components and utilities

### Process Model
Lightweight Thread Package::an application-level construct that supports multiple threads within single OS process
DBMS client::software component that implements API to communicate with DBMS. API example: JDBC, ODBC..
DBMS Worker::the thread of execution in DBMS that work on behalf of DBMS client with 1:1 mapping between client and worker.

#### Process per DBMS Worker

13/119
