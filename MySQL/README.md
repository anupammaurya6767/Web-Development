# SQL --> Structured Query Language

<img alt="MYSql" src="https://img.shields.io/badge/-mySQL-orange?style=flat-square&logo=mysql&logoColor=white"/>

SQL is a database computer language designed for the retrieval and management of data in a relational database. 

# CRUD Operartion in My SQL (Create Read Update Delete)

 ## To create a table 
 
 ```
    CREATE TABLE <table name>
    {
      id INT NOT NULL,
      name STRING,
      price MONEY, // MONEY  is a datatype in MySQL
      PRIMARY KEY(id) // settinf one of the field as primary key
    }
 ```
 
 ## For insertion into table
 
 ```
    INSERT INTO <table name>
    VALUES (1,"pen",1.20)
 ```
 
 ```
   INSERT INTO <table name> (id,name)
   VALUES (2,"pencil")  // when to skip some value
 ```
 
 ## To read a data from database
 
 ```
    SELECT * FROM <table name> WHERE id=1  // WHERE for a particular data
 ``` 
 
 ## To update a data in database
 
 ```
    UPDATE <table name>
    SET price = 0.80
    WHERE id = 2
    
 ```
 
 ## To modify the table 
 
 ```
    ALTER TABLE <table name> 
    ADD stock INT  // add another column
 ```
 
 ## To delete a data from database
 
 ```
    DELETE FROM <table name>
    WHERE <condition>
 ```
 
