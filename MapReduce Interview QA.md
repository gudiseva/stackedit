## MapReduce Interview Questions and Answers

Q. MR code explanation for emp table find the avg salary

Q. What is MapReduce?
Map reduce is NOT for cleaning data!!!  rather  it is meant to analyze the data to find the trends and prepare the data for further analysis.

Q. Sequence FileInputFormat example
Reference: http://www.programcreek.com/java-api-examples/index.php?api=org.apache.hadoop.mapreduce.lib.input.SequenceFileInputFormat

Q. Can we set the no.of mappers in MR program?  Is it possible?
No, it completely depends upon input split.  We can set map task instance but in some conf file.

Q. Wait for Submission; Submit job and exit
Ans. Mappers cannot talk to each other.  Only at Shuffling and Sorting they come to see each other.
MR gives good control of patterns compared to Pig and Hive
Joins are expensive.

Q. Projection -> Transfer only what is required
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgwMTU0NDIyOSwtMTA1MTgxMTkwM119
-->