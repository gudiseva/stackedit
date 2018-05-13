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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTYyMjcxODYsLTI2NzY2NzEwMiwtMT
kzNjc5MDI5NSwxODE2NzY2NDcxLDI5NjkwNTExMl19
-->