# Lombok

Add lombok as a dependency. (add the code in the dependecies part of *pom.xml*)

```xml
<!-- https://mvnrepository.com/artifact/org.projectlombok/lombok-maven -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.16.12</version>
        </dependency>
```

[Here is a good tutorial](https://gualtierotesta.wordpress.com/2014/03/03/tutorial-using-lombok-to-reduce-boilerplate-code-in-java/)

Errors will appear in intelij. To make the ide aware of lombok the following plugin should be installed: https://plugins.jetbrains.com/plugin/6317-lombok-plugin

# Mysql

To inspect tables and date, *mysql workbench* should be used

# Mysql and spring


Here is an official tutorial combining [Spring and mysql.](https://spring.io/guides/gs/accessing-data-mysql/)

A more detailed one is [this.](http://blog.netgloo.com/2014/10/27/using-mysql-in-spring-boot-via-spring-data-jpa-and-hibernate/)

# Model mapper

Manually setting object fields is tedious. Developers use a mapper which tries to automatically convert from one object to another. (Tutorial)[http://modelmapper.org/getting-started/]

# Mysql and spring project (project)

The mysql schema should consist of the following tables:

Actor:
+ id (primary key, auto increment, int)
+ name (varchar(20))
+ age (integer type)
+ email ()

Movie:

+ id (primary key, auto increment, int)
+ name (char(20))
+ release date (date/timestamp)
+ revenue (name)

Features:

+ The backend should permit crud (create, read, update, delete) for both. Also a short path with just id and name for both.

+ Controller should only return dto's.

+ Lombok will be used to generate getters and setters.

+ Use modelmapper for entity to dto conversion.

