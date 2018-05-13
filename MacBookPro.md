# Mac Book Pro Command

## Hadoop Usage

$ java -version
$ javac -version

$ scala -version
$ sbt sbtVersion
$ sbt scalaVersion

$ vim ~/.bash_profile

$ hadoop version
$ hdfs dfsadmin -report
$ hdfs namenode -format

$ Enable SSHd
$ ssh-keygen -t rsa -P ""
$ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
$ ssh localhost

$ start-dfs.sh
$ start-yarn.sh
$ jps

$ hdfs dfs -mkdir /user
$ hdfs dfs -mkdir /user/gudiseva

Hadoop Web Interface URL: http://localhost:50070/

$ stop-yarn.sh
$ stop-dfs.sh
$ jps

$ spark-shell
scala> :q

Spark Web Interface URL: http://localhost:4040/

$ spark-sql
spark-sql> show databases;
spark-sql> show tables;
spark-sql> exit;


$ hive
hive> show databases;
hive> show tables;
hive> exit;

$ pig
grunt> quit
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTgyODg5MDVdfQ==
-->