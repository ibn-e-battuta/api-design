# Database Design Fundamentals

## What is a database?

A database is a shared collection of **related data**. By **data**, we mean known facts that can be recorded and that have implicit meaning.

A database can be viewed as a repository of data that is defined once and then accessed by various users.

### Database properties

- A database represents some aspect of the real world, sometimes called the *mini-world* or the **universe of discourse** (**UoD**). Changes to the mini-world are reflected in the database.

- A database is a **logically coherent collection of data** with some inherent meaning. A random assortment of data cannot correctly be called a database. For example, a list of random names cannot be considered a database but if we also note down those peoples’ addresses and phone numbers, then the data will have some inherent meaning (i.e. it will be an address book).

- A database is designed, built, and populated with data for a specific purpose. It has an intended group of users and some preconceived applications in which these users are interested. For example, a department in a university might be interested in gathering data regarding the students’ GPA so that they can finalize the dean’s honor list.

In other words, a database has some degree of interaction with events in the real world and an audience that is actively interested in its contents. The users of a database may perform some transaction or events may happen.

## Database management systems (DBMS)

If an organization wants to adopt the database approach, then it needs a collection of programs that enable the users of the organization to create and maintain databases and control all access to them. This is achieved using a **database management system** (DBMS). The primary goal of a DBMS is to provide an environment that is both convenient and efficient for users to retrieve and store information.

### Facilities provided by a DBMS

- **Defining** a database involves defining the data types, structures, and constraints of the data to be stored in the database.

- **Constructing** the database is the process of storing the data on a storage device that is controlled by the DBMS.

- **Manipulating** a database involves querying the database to retrieve specific data, updating the database, etc.

- **Sharing** a database allows multiple users and programs to access the database simultaneously.

> A **table** is a collection of related data held in a table format within a database. It consists of columns and rows.

> Each row in a relational database represents one instance of the type of object described in that table. A row is also called a **record**. While the columns in a table are the set of facts that we keep track of regarding that type of object. A column is also called an **attribute**.

## Characteristics of a database

1. Self-describing nature of a database system

    A database system is self-describing because it not only contains the database itself, but also the meta-data which defines and describes the data and relationships between tables in the database. This information is stored in a catalog by the DBMS software.  

2. Insulation between program and data

In the file-based system, the structure of the data files is defined in the application programs so if a user wants to change the structure of a file, all the programs that access that file might need to be changed as well.

On the other hand, in the database approach, the data structure is stored in the system catalog and not in the programs. Therefore, one change is all that is needed to change the structure of a file. This insulation between the programs and data is also called **program-data independence**.

For example, we have an application program that is designed to work with the current structure of the STUDENT table. If we want to add another piece of data to the STUDENT table, say a column called Home_Address, such a program will no longer work and would have to be changed.

On the other hand, in a DBMS environment, we only need to change the description of the STUDENT table in the catalog to reflect the inclusion of the new data item Home_Address in each student record. So the next time a DBMS program refers to the catalog, the new structure of the STUDENT table will be used.
3. Support for multiple views of data

A database supports multiple views of data. A view is a subset of the database, which is defined and dedicated for particular users of the system. Multiple users in the system might have different views of the system. Each view might contain only the data of interest to a user or group of users. For example, one user of the university database may be interested only in accessing the names of the professors in each department. The view for this user is shown below:
Department_code 	Department_name 	Instructor_name
		Sam Winchester
1 	Computer Science 	Doug Waterman
		Glen Orsburn
		
		Dean Wright
2 	Electrical Engineering 	Terri Keane
		James Avery

The user will only be presented with the relevant information rather than the whole database.
4. Sharing data and multiuser system

Current database systems are designed for multiple users. That is, they allow many users to access the same database at the same time. This access is achieved through features called concurrency control strategies. These strategies ensure that the data accessed are always correct and that data integrity is maintained. Consider the case when multiple reservation agents try to assign a seat on an airline flight, the DBMS should ensure that each seat can be accessed by only one agent at a time so that the same seat is not assigned to multiple passengers.

---

## Data Modelling

In order to store data in a database system, we need some data-structures. Hence the database systems we use normally include some complex data structures which we normally do not use. To make the system efficient in terms of data retrieval, and reduce complexity in terms of usability, developers use data abstraction i.e., hide irrelevant details from the users.

In order to achieve this abstraction, we use **data models**.

> A data model is a collection of concepts or notations for describing data, data relationships, data semantics, and data constraints.

## Types of data models

The different types of data models can be classified into the following categories:

1. High-level conceptual data models

    High-level conceptual data models provide a way to present data that is similar to how people perceive data. A typical example is an entity-relationship model, which uses concepts like entities, attributes, and relationships.

    **Entity relationship model**

    An **entity** represents a real-world object such as an employee or a project. The entity has **attributes** that represent properties such as an employee’s name, address, and birth-date. A **relationship** represents an association among entities; for example, an employee works on many projects. A relationship exists between the employee and each project.

2. Record-based logical data models

    Record-based logical data models provide concepts users can understand but are still similar to the way data is stored on the computer. Three well-known data models of this type are: hierarchical, network, and relational data models.
Hierarchical model

In a hierarchical model, data is organized into a tree-like structure, implying a single parent for each record. This structure mandates that each child record has only one parent, whereas each parent record can have one or more child records. This concept is illustrated below:
Car is the parent of both Engine and Body, so each child has only one parent.
Car is the parent of both Engine and Body, so each child has only one parent.
Network model

The network model expands upon the hierarchical structure, allowing each record to have multiple parent and child records, forming a generalized graph structure. It was the most popular model before being replaced by the relational model. The network model is shown in the diagram below:
In this figure, we can see that the Subject is the child of Student and Degree. So, it has two parent classes.
In this figure, we can see that the Subject is the child of Student and Degree. So, it has two parent classes.
Relational model

The relational model represents data as relations or tables. For example, the university database system contains multiple tables (relations) which in turn have several attributes (columns) and tuples (rows).
3. Physical data models

The physical data model represents how data is stored in computer memory, how it is scattered and ordered in the memory, and how it would be retrieved from memory. Basically physical data model represents each table, its columns, and specifications, etc. It also highlights how tables are built and related to each other in the database. The diagrammatic representation of physical models is shown below:
The STUDENT table is related to the DEPARTMENT table through the Dep_Id attribute.
The STUDENT table is related to the DEPARTMENT table through the Dep_Id attribute.

As we can see the STUDENT table consists of attributes like Std_Id, Std_Name, Age etc. along with their data type. Same for the DEPARTMENT table. The arrow simply shows how these two tables are connected in this model.

---

## Entity-Relationship Data Model

The **entity-relationship** (**ER**) data model is a high-level conceptual data model that has existed for over 35 years. It is well suited to data modeling for use with databases because it is fairly abstract and is easy to discuss and explain. ER models, also called ER schemas, are represented by **ER diagrams**.

ER modeling is based on two concepts:

- **Entities**, defined as tables that hold specific information (data).
- **Relationships**, defined as the associations or interactions between entities.

Here is an example of how these two concepts might be combined in an ER data model: **Prof. Lawrence** (*entity*) **teaches** (*relationship*) **the database systems course** (*entity*).