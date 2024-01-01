+++
title= "Learnings of the Day 01/01"
date= '2024-01-01'
draft= 'false'
tags= [""]
categories= ["Others"]
+++

## SQL
SQL (Structured Query Language) is a language used for managing and manipulating relational databases. Here are some fundamental SQL commands:

### 1. **CREATE DATABASE:**
   - **Usage:**
     ```sql
     CREATE DATABASE database_name;
     ```
   - **Description:**
     Creates a new database with the specified name.

### 2. **USE:**
   - **Usage:**
     ```sql
     USE database_name;
     ```
   - **Description:**
     Switches to the specified database, making it the active database for subsequent operations.

### 3. **CREATE TABLE:**
   - **Usage:**
     ```sql
     CREATE TABLE table_name (
         column1 datatype,
         column2 datatype,
         ...
     );
     ```
   - **Description:**
     Creates a new table with the specified columns and data types.

### 4. **INSERT INTO:**
   - **Usage:**
     ```sql
     INSERT INTO table_name (column1, column2, ...)
     VALUES (value1, value2, ...);
     ```
   - **Description:**
     Adds a new row of data into the specified table.

### 5. **SELECT:**
   - **Usage:**
     ```sql
     SELECT column1, column2, ...
     FROM table_name
     WHERE condition;
     ```
   - **Description:**
     Retrieves data from one or more columns in a table based on specified conditions.

### 6. **UPDATE:**
   - **Usage:**
     ```sql
     UPDATE table_name
     SET column1 = value1, column2 = value2, ...
     WHERE condition;
     ```
   - **Description:**
     Modifies existing data in a table based on specified conditions.

### 7. **DELETE:**
   - **Usage:**
     ```sql
     DELETE FROM table_name
     WHERE condition;
     ```
   - **Description:**
     Removes rows from a table based on specified conditions.

### 8. **ALTER TABLE:**
   - **Usage:**
     ```sql
     ALTER TABLE table_name
     ADD column_name datatype;
     ```
   - **Description:**
     Modifies the structure of an existing table, such as adding a new column.

### 9. **DROP TABLE:**
   - **Usage:**
     ```sql
     DROP TABLE table_name;
     ```
   - **Description:**
     Deletes an existing table and all its data.

### 10. **CREATE INDEX:**
   - **Usage:**
     ```sql
     CREATE INDEX index_name
     ON table_name (column1, column2, ...);
     ```
   - **Description:**
     Creates an index on one or more columns of a table to improve query performance.

### 11. **GRANT:**
   - **Usage:**
     ```sql
     GRANT permission
     ON table_name
     TO user_name;
     ```
   - **Description:**
     Provides specific permissions to a user for a particular table.

### 12. **REVOKE:**
   - **Usage:**
     ```sql
     REVOKE permission
     ON table_name
     FROM user_name;
     ```
   - **Description:**
     Removes specific permissions from a user for a particular table.

SQL commands that cover database creation, table manipulation, data retrieval, and user permissions. SQL is a vast language, and these commands provide a foundation for working with relational databases.