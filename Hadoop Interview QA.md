# Hadoop Interview Questions and Answers


Q. Difference between Cloudera and Hortonworks?

Q. What is federation and fencing?
Fencing:  In a high availability configuration, during an unexpected failover the previously active NN  could still be running and could still think & act as an active NN. Even though the cluster would be now controlled by the standby NN. Fencing is a method to prevent the previously active NN from doing any damage or corruption to the HDFS namespace during any unexpected failover. Here are couple of widely used fencing methods.
Federation: Combination of namenodes. More than one name node in a cluster called federation.

Q. Speculative execution
 - Job Tracker receives heart beat from Task Tracker (every 3 Secs).  It waits for 10 cycles and kicks off another Task Tracker with redundancy.
 - The first output from the redundant task trackers are considered and the rest are abandoned.
    
Q. HUE
 - Antonym of Hadoop User Environment
 - Hue is a set of web applications that enable you to interact with a CDH cluster. Hue applications let you browse HDFS and work with Hive and Cloudera Impala queries, MapReduce jobs, and Oozie workflows.
 - Apache hue is the portal to manage the Big Data Tools

Q. Talend with big data
http://download-mirror1.talend.com/tosbd/release/V6.1.0M1/TOS_BD-20150812_1515-V6.1.0M1.zip?_ga=1.193450349.1134014040.1439550379

Q. How do we transfer data from NoSql databases into HDFS?  Which tool do we use?

Q. Name Node
 - Receives blocks information and heartbeats (every 10 Secs) from Data Nodes
 - SPF.  If down, can't access HDFS
 - Master daemon for creating metadata for blocks

Q. Data Replication
 - Block replication happens among Data Nodes.  They do not communicate via Name Node.
 - NN takes the responsibility to replicate data in case of dead nodes

Q. Fault Tolerance
 - Default replication of 3

Q. Default Replication Factor
 - 3 (set in hdfs-site.xml)
 - Mandatory that 1 rack must have 1 replication; another rack must have 2 replications

Q. HDFS Block  Size
 - Default Block size is 64 Mb
 - 200 MB file is split into 4 input splits (3 x 64Mb Blocks + 1 x 8Mb Blocks). Remaining space (64Mb - 8Mb = 56Mb) will be used for some other file

Q. Data Locality
 - Every Task Tracker works on Data which is local to the Data Node
 - Mapper has data locality
 - Reducer never has data locality

Q. Difference between CDH3 and CDH4
 - CDH4 has 2 NameNodes.  If active NN fails, standby NN picks up.

Q. How is Input Split calculated?  Is it dependent on the Block Size?
	E.g. 1 GB is the File size.  HDFS Block Size is 128 MB.  256 MB is the Input Split

Q. YARN child?

Q. Daemons running on Hadoop cluster? 
 E.g. 10 GB, 2 Data node, 8GB of memory, 1TB of HDD

Q. Distributed cache

Q. Difference Hadoop 1 and Hadoop 2?
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkzNjY5NzM2NiwxODcxMTg1MzcyXX0=
-->