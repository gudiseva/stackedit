# Hive Interview Questions

Q. What is hive metastore?

Q. Difference between managed and external tables?
Yeh its like if you want multiple tool and multiple users to operate on your data at the same time than create an external table
As all the data ultimately stored on files on hdfs
Another difference:-
When you drop an internal table, it drops the data, and it also drops the metadata.
When you drop an external table, it only drops the meta data. That means hive is ignorant of that data now. It does not touch the data itself.


Q. UDF's in Pig and Hive?  When is it used?

Q.  When to choose Hive or Pig in the project?
 
Q. Difference between Buckets and Partitions?

Q. How to implement slowly changing dimensions data in hive?
Slowly changing means dynamic data right?
Yup...it will come in informatica..but how v can achieve in hive
For dynamic data we have to integrate with hbase I think coz hive is only for olap

Q. Hive - Hbase Integration - using storagehandlers
So the data is present in hbase, now create table in hive with stored by org.apache.Hadoop.hive.hbase.hbasestoragehandler
With serde properties next tblproperties
So backend table is hbase.  Mirror is hive

Q. EXPLODE function in hive?
http://www.cnblogs.com/linehrr-freehacker/p/3309088.html
To arrange one element in each row of array...they ll use explode..it ll be in ascending order

Q. Cost based optimization; Calcite

# Sagarsoft
1. Set mappers in Hive
2. Set reducers in Hive
3. How many mappers are created?
4. Errors / Failures in Hive
5. Clustered By, Partitioned By
https://www.guru99.com/hive-queries-implementation.html
6. Map Joins
7. Merge Sort
8. How do you handle Data skew
9. Hive Performance tuning parameters
10. Tez - Hortonworks optimize Hive on Tez
11. Max Date in Hive -> Convert to UNIX Timestamp and apply Max on that column
12. Filter only on Weekdays
SELECT FROM_UNIXTIME(UNIX_TIMESTAMP('2018-04-18 00:00:00'), 'EEEE');
SELECT DATE1, FROM_UNIXTIME(UNIX_TIMESTAMP(DATE1, 'YYYY-MM-DD'), 'E') FROM DATETODAY;
DESC DATETODAY;

## Pluralsight :: 
Q. What command would you use to add partition data from a location on HDFS, to an existing EXTERNAL table?
Ans. alter table Reviews add partition (category="Fashion") location '/tables/reviews/Fashion'

Q. Why does hive.exec.dynamic.partition.mode=nonstrict need to be set when using all dynamic partitions in Hive?
Ans. The default mode is the strict mode which requires that the table have at least one static partition.

Q. Which of the following is an advantage of bucketing tables?
Ans. Join operations can run faster as records can be looked up more quickly.

Q. Why is bucket sampling more efficient than other ways of sampling Hive table data?
Ans. It scans only the records in a single bucket and not the entire table for sample records.

Q. Consider an e-commerce site with these tables

    Orders
    - order id
    - product id
    - customer id
    - quantity
      
    Products
    - product id
    - product name
    - cost
      
    Reviews
    - review id
    - product id
    - order id
    - username
    - category  

The sizes of the tables are as follows:

    Orders: 100GB
    Products: 500MB
    Reviews: 1GB  

If you had to join all 3 tables together what is the order in which you would specify the tables in the join operation in order to have the fastest join?
Ans. Products, Reviews, Orders

Q. Why is the left semi-join faster than the IN/EXISTS subqueries?
Ans. The left semi-join scans the table on the right side of the join only until the matching record is found, it does not scan the entire table.

Q. How would you specify a window between the first row in a result set and the current row?
Ans. rows between unbounded preceding and current row

Q. How would you specify a window which included exactly 5 records as it moves over the results?
Ans. rows between 4 preceding and current row

Q. Why do analysts not use MapReduce for all their data processing needs?
Ans. MapReduce is not very accessible as it requires coding in a language such as Java and Python.

Q. All of these are good reasons to use Hive for data processing EXCEPT:
Ans. 
-   Hive runs MapReduce under the hood, and abstracts away all the complexity of running MapReduce jobs.
-   Hive uses HiveQL, a query language very similar to SQL which makes it accessible and easy to use.
 -  Hive runs on Hadoop and uses its distributed computing environment to process large datasets.

Q. Which of these is an advantage of using window functions?
Ans.
- Eliminates the use of intermediate tables and temporary data  
- Allows complex queries to be expressed more simply
- Eliminates the use of a script for certain operations and reduces them to a single query

Q. What is the command to see what partitions exist in a Hive table?
Ans.
show partitions `<tablename>`

Q. Consider a table storing information on product reviews on an e-commerce site. The table named Reviews contains the following information:

    Reviews
    - id
    - username
    - text
    - product id
    - category
    - date  

Let's say this table is partitioned on the product  **category**  column.

How will the directory structure look in this Reviews table?
Ans. 

    Reviews
        - category=Mobiles (directory)
             - 0000-0 (file)
             - 0000-1(file)
        - category=Fashion (directory)

Q. Which of these is a difference between bucketing and partitioning?
Ans.
-  The number of buckets in a table is fixed while the number of partitions depends on the data.
-  Buckets are usually around the same size, partition sizes can vary greatly.
-  Bucketing is based on a hash value of a column and partitioning is based on actual column values.
Q. Which of the following are the ways to sample data from Hive tables?
Ans.
-   Bucket Sampling
-   The LIMIT Keyword
-   Block Sampling
-   Row Count Sampling
Q. Which of the following are the reason that map-only joins are faster than joins which run both map and reduce phases?
Ans.
-  Complete MapReduce operations have additional steps such as shuffle and sort between the map and reduce phases which gets eliminated in map-only joins.
-  Improved processing time because one phase is entirely eliminated.
-  Map-only joins reduce data transfer within a cluster.

Q. When the table on the right side of a join operation is much smaller than the table on the left side of a join operation, which of the following are map-only joins?
Ans.
-  Left-outer join

Q. What keyword would you use to run a window operation on logical groups of data e.g. grouped on the category column of a table?
Ans. partitioned by category

Q. Analytical processing jobs include all of these characteristics:
Ans.
-   Works on huge datasets from multiple sources
-   Tends to involve long running jobs
-   Reads data, does not usually edit or update it

Q. Which are possible ways in which join performance can be optimized?
Ans. Structuring joins such that the reduce phase of the underlying MapReduce is eliminated.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMjEyOTIzMTQsMTY4MTc2NDA5MiwtMz
YzODQzNjU2LC0yNjc2NjcxMDIsLTE5MzY3OTAyOTUsMTgxNjc2
NjQ3MSwyOTY5MDUxMTJdfQ==
-->