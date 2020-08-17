# Big Table-*like* Database Management System Implementation
<!-- TABLE OF CONTENTS -->
## Table of Contents
  * [About the Project](#about-the-project)
  * [Introduction](#introduction)
  * [Built With](#built-with)
  * [Terminology](#terminology)
  * [Schema](#schema)
  * [Operations](#operations)
  * [Advantages](#advantages)
  * [Data](#data)

<!-- ABOUT THE PROJECT -->
## About The Project
The goal of this project is to implement a BigTable-*like* Database Management system using [MiniBase](https://research.cs.wisc.edu/coral/mini_doc/minibase.html) modules.

## Introduction
[Big table](https://en.wikipedia.org/wiki/Bigtable) is a high performance data storage system built on Google File Systems. The data in Big table is stored in the form of key-value pairs along with time-stamps to achieve versioning. This project focuses on implementing various functionalities of a database management system for Big Table.  

## Built With
* Java
* Eclipse IDE
* Sublime<br/>

## Terminology
* **Map:** A Map is a data structure which contains attributes that make up a relation. A *Map* comprises of 4 attributes: *Row Label, Column Label, Timestamp, and Value*.   
* **B+ tree:** A tree based indexing structure basically used for range queries. Every internal node of a tree can have multiple records in the form of a key and a pointer.    
* **Big Table:** This is a distributed and persistent multi- dimensional sorted map. The map is indexed by a row key, column key, and a timestamp.
* **Index:** An index is a set of ordered references to rows of a table. Index can improve the query execution time in a database by reducing the number of physical pages that a database can access.   
 * **B-Tree Index**: 
   * **On Clustered Index:** B-tree index is a balanced and shallow tree-structured index in which records are present at the last level. In this the records are sorted in the last level of index.  
   * **On Un Clustered Index:** B-tree index is a balanced and shallow tree-structured index in which the last level of tree consists of key-value pairs. In this, the last level has a pointer which points to the respective map.  
 * **Heap File:** A heap file consists of set of unsorted records.
* **External Sort:** [External sorting](https://www.geeksforgeeks.org/external-sorting/) is a technique in which the data is stored on the secondary memory. In the sorting phase, chunks of data small enough to fit in main memory are read, sorted, and written out to a temporary file. In the merge phase, the sorted sub-files are combined into a single larger file.  

## Schema
* BigDB corresponds to the database which in turn contains Big Tables with an indexing strategy. Each Big Table contains a heap file and index files.  
* The data in this system is stored in database objects which are called as *Big Tables*. This table is basically a collection of records called *Maps*. These Maps replaces tuples in a traditional relational database.  
* In each big table, Maps can be sorted and stored according to 5 different storage types(*clustering and indexing strategies*), based on the Batch/Map insert. 
  * In Type 1, Maps will be stored randomly. 
  * In Types 2 and 3, Maps will be sorted and stored based on row and column labels respectively. 
  * In Types 4 and 5 , Maps will be sorted and stored based on the combined key used for (column label, row label) and (row label, value) indexes.
* There can be atmost 3 maps with the same row and column label, but different timestamps, in the entire Big Table – irrespective of which batch they were inserted in and which storage type they were subjected to.  
* At the end of each query operation, the program returns the number of  disk reads and writes which can be used to measure the performance of the system.

## Operations
* **Batch Insert**: This operation is to insert a bulk amount of data (Maps) into an existing Big Table or a new Table in the database.
* **Map Insert**: This operation is to insert a single Map into an existing Big Table or a new Table in the database.
* **Data Filtering:** Data can be filtered using a single value(*Equality Search*) or a range of values(*Range Search*) or NULL on any of the row label, column label and value attributes.
* **Data Retrieval:** Data can be queried, filter and retrieved using 5 different strategies(*Order-by types*).
* **Row-Join:** A row join command to access and row-joins two bigT tables based on the column label provided and creates a new resultant bigT table.
* **Row-Sort:** An external row sort operation in which rows are sorted according to the most recent values for a given column label.
* **Get Count:** To get the total number of Maps, distinct row labels, and distinct column labels accross the database.
* **Delete Table:** Delete the bigtable from the database.

## Advantages
* Flexible Schema
* Composite Indexing
* Priority-based External Sorting
* Organized distribution of data in columns
* Ordering of the data can be maintained with the help of the timestamp column which can boost up the retrieval of records in the table.

## Data
* An excel sheet that contains row label, column label, value and timestamp in different columns.
