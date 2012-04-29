greenvine-demo
==============

A template for creating a greenvine reverse engineering project.

Download or clone this project and then modify it to point to the database you want to reverse engineer.

Quickstart
----------
1. Clone or download the zip of this project and expand somewhere.
2. Open a terminal and cd to the directory of the downloaded/expanded template project folder.
3. Have a look at the demo database in your preferred text editor. It's located in:
    src/main/greenvine/schedule_schema.sql
4. Use the SQL Maven Plugin to build the demo database, which is a H2 in memory database. To do this, simply type:
    mvn sql:execute
5. Now you are ready to test Greenvine. To reverse engineer the database you created and generate code type:
    mvn greenvine:revgen
6. Watch the terminal for output. When it's finished, change directory to the generated source to see what was output.
   cd target/generated-sources/greenvine
7. You should see a full Maven project with main and test classes for JPA and Hibernate based on the demo schema.
8. To build and run the tests of the demo project, type:
   mvn test

Getting Started
---------------
Once you have taken the test database for a spin, you might want to try it with your own database and schema. Although the demo database is a H2 in memory database, the tool should work with any JDBC database.

This is done by modifying the src/main/greenvine/db-extractory-ctx.xml file. It's a Spring configuration file, but you don't need to know Spring. The properties are reasonably self-evident.

The most obvious change is to set the JDBC driver and properties for the database you want to reverse engineer. 

There are also settings to modify the extractor to match any naming conventions in your database that you don't want in the final Java code.

For example, table prefixes or suffixes. You will probably need to experiment with these settings to get the best results.

Note that it is possible to name your database objects with reserved words in Java which will cause compilationm problems.
