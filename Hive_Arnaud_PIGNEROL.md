# Hive Beeline Client

## 1.1 Create a Connection to Beeline Client

### Connect to HADOOP cluster using SSH
```CMD
-sh-4.2$ ssh apignerol@hadoop-edge01.efrei.online
Welcome to EFREI Hadoop Cluster

Last login: Tue Nov 10 09:57:59 2020 from 65-101-97-185.ftth.cust.kwaoo.net
```

### Initialize a Kerberos ticket
```CMD
-sh-4.2$ kinit
Password for apignerol@EFREI.ONLINE:
```

### Type the command beeline in the terminal prompt, when prompted press enter as username and as password.
### Connect to the Hive using the command !connect
```CMD
-sh-4.2$ beeline

SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/usr/hdp/3.1.5.0-152/hive/lib/log4j-slf4j-impl-2.10.0.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/usr/hdp/3.1.5.0-152/hadoop/lib/slf4j-log4j12-1.7.25.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [org.apache.logging.slf4j.Log4jLoggerFactory]
Connecting to jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/default;httpPath=cliservice;principal=hive/_HOST@EFREI.ONLINE;serviceDiscoveryMode=zooKeeper;ssl=true;transportMode=http;zooKeeperNamespace=hiveserver2
20/11/10 10:05:44 [main]: INFO jdbc.HiveConnection: Connected to hadoop-master03.efrei.online:10001
Connected to: Apache Hive (version 3.1.0.3.1.5.0-152)
Driver: Hive JDBC (version 3.1.0.3.1.5.0-152)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 3.1.0.3.1.5.0-152 by Apache Hive

0: jdbc:hive2://hadoop-master01.efrei.online:> !connect jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=hiveserver2
Connecting to jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=hiveserver2

Enter username for jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/:
Enter password for jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/:
20/11/10 10:09:05 [main]: INFO jdbc.HiveConnection: Connected to hadoop-master03.efrei.online:10001
Connected to: Apache Hive (version 3.1.0.3.1.5.0-152)
Driver: Hive JDBC (version 3.1.0.3.1.5.0-152)
Transaction isolation: TRANSACTION_REPEATABLE_READ
```


### Type help command for list of beeline commands.
```CMD
1: jdbc:hive2://hadoop-master01.efrei.online:> help

!addlocaldriverjar  Add driver jar file in the beeline client side.
!addlocaldrivername Add driver name that needs to be supported in the beeline
                    client side.
!all                Execute the specified SQL against all the current connections
!autocommit         Set autocommit mode on or off
!batch              Start or execute a batch of statements
!brief              Set verbose mode off
!call               Execute a callable statement
!close              Close the current connection to the database
!closeall           Close all current open connections
!columns            List all the columns for the specified table
!commit             Commit the current transaction (if autocommit is off)
!connect            Open a new connection to the database.
!dbinfo             Give metadata information about the database
!delimiter          Sets the query delimiter, defaults to ;
!describe           Describe a table
!dropall            Drop all tables in the current database
!exportedkeys       List all the exported keys for the specified table
!go                 Select the current connection
!help               Print a summary of command usage
!history            Display the command history
!importedkeys       List all the imported keys for the specified table
!indexes            List all the indexes for the specified table
!isolation          Set the transaction isolation for this connection
!list               List the current connections
!manual             Display the BeeLine manual
!metadata           Obtain metadata information
!nativesql          Show the native SQL for the specified statement
!nullemptystring    Set to true to get historic behavior of printing null as
                    empty string. Default is false.
!outputformat       Set the output format for displaying results
                    (table,vertical,csv2,dsv,tsv2,xmlattrs,xmlelements, and
                    deprecated formats(csv, tsv))
!primarykeys        List all the primary keys for the specified table
!procedures         List all the procedures
!properties         Connect to the database specified in the properties file(s)
!quit               Exits the program
!reconnect          Reconnect to the database
!record             Record all output to the specified file
!rehash             Fetch table and column names for command completion
!rollback           Roll back the current transaction (if autocommit is off)
!run                Run a script from the specified file
!save               Save the current variabes and aliases
!scan               Scan for installed JDBC drivers
!script             Start saving a script to a file
!set                Set a beeline variable
!sh                 Execute a shell command
!sql                Execute a SQL command
!tables             List all the tables in the database
!typeinfo           Display the type map for the current connection
!verbose            Set verbose mode on

Comments, bug reports, and patches go to ???
```

### Which command allows you to view the jdbc connection used to connect to HiveServer2?
```CMD
1: jdbc:hive2://hadoop-master01.efrei.online:> !list

1 active connections:
 #0  open     jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/default;httpPath=cliservice;principal=hive/_HOST@EFREI.ONLINE;serviceDiscoveryMode=zooKeeper;ssl=true;transportMode=http;zooKeeperNamespace=hiveserver2
```

### List all databases.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> show databases

. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201110103823_e1d611dc-60d5-4080-a70f-c5e02ba1bc4c): show databases
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201110103823_e1d611dc-60d5-4080-a70f-c5e02ba1bc4c); Time taken: 0.005 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201110103823_e1d611dc-60d5-4080-a70f-c5e02ba1bc4c): show databases
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201110103823_e1d611dc-60d5-4080-a70f-c5e02ba1bc4c); Time taken: 0.007 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+--------------------+
|   database_name    |
+--------------------+
| aledeuf            |
| apignerol          |
| cloupec            |
| comnes             |
| cspatz             |
| database_ccarayon  |
| default            |
| egueuret           |
| mbury              |
| psalvaudon         |
| table_hive         |
| table_test         |
| temp               |
| ttea               |
| vgonnot            |
+--------------------+
```

### If not exists, create a database using your username.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> create database if not exists apignerol

. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201110104359_283fa439-6e9d-462a-b30f-b60299c03e77): create database if not exists apignerol
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20201110104359_283fa439-6e9d-462a-b30f-b60299c03e77); Time taken: 0.001 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201110104359_283fa439-6e9d-462a-b30f-b60299c03e77): create database if not exists apignerol
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201110104359_283fa439-6e9d-462a-b30f-b60299c03e77); Time taken: 0.075 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.095 seconds)
```

### Use your database.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> use apignerol

. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201110110033_42568c28-6f91-4acf-847b-042a8224c4bb): use apignerol
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20201110110033_42568c28-6f91-4acf-847b-042a8224c4bb); Time taken: 0.018 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201110110033_42568c28-6f91-4acf-847b-042a8224c4bb): use apignerol
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201110110033_42568c28-6f91-4acf-847b-042a8224c4bb); Time taken: 0.016 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.055 seconds)
```

### List the tables.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> !tables

+------------+----------------+-----------------+-------------+----------------+-----------+-------------+------------+----------------------------+-----------------+
| TABLE_CAT  |  TABLE_SCHEM   |   TABLE_NAME    | TABLE_TYPE  |    REMARKS     | TYPE_CAT  | TYPE_SCHEM  | TYPE_NAME  | SELF_REFERENCING_COL_NAME  | REF_GENERATION  |
+------------+----------------+-----------------+-------------+----------------+-----------+-------------+------------+----------------------------+-----------------+
|            | aledeuf        | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | aledeuf        | trees_internal  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | aledeuf        | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | comnes         | trees_internal  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | comnes         | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | aledeuf         | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | trees_internal  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | treesexternal   | TABLE       | Trees dataset  | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | idelaronciere  | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | lboumriche     | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | mbury          | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | vgonnot        | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | vserena        | treesexternal   | TABLE       | Trees dataset  | NULL      | NULL        | NULL       | NULL                       | NULL            |
+------------+----------------+-----------------+-------------+----------------+-----------+-------------+------------+----------------------------+-----------------+
```

### Create table called temp with a column called col of String type.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> create table if not exists temp(col String)

. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201110114242_823579e1-e614-4538-9c21-f0254b988f91): create table if not exists temp(col String)
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20201110114242_823579e1-e614-4538-9c21-f0254b988f91); Time taken: 0.01 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201110114242_823579e1-e614-4538-9c21-f0254b988f91): create table if not exists temp(col String)
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201110114242_823579e1-e614-4538-9c21-f0254b988f91); Time taken: 0.064 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.088 seconds)
```

### Confirm the table creation.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> !tables

+------------+----------------+-----------------+-------------+----------------+-----------+-------------+------------+----------------------------+-----------------+
| TABLE_CAT  |  TABLE_SCHEM   |   TABLE_NAME    | TABLE_TYPE  |    REMARKS     | TYPE_CAT  | TYPE_SCHEM  | TYPE_NAME  | SELF_REFERENCING_COL_NAME  | REF_GENERATION  |
+------------+----------------+-----------------+-------------+----------------+-----------+-------------+------------+----------------------------+-----------------+
|            | aledeuf        | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | aledeuf        | trees_internal  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | aledeuf        | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | apignerol      | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | comnes         | trees_internal  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | comnes         | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | aledeuf         | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | trees_internal  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | default        | treesexternal   | TABLE       | Trees dataset  | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | idelaronciere  | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | lboumriche     | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | mbury          | trees_external  | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | vgonnot        | temp            | TABLE       | NULL           | NULL      | NULL        | NULL       | NULL                       | NULL            |
|            | vserena        | treesexternal   | TABLE       | Trees dataset  | NULL      | NULL        | NULL       | NULL                       | NULL            |
+------------+----------------+-----------------+-------------+----------------+-----------+-------------+------------+----------------------------+-----------------+
```

### List the columns (name, data type, etc) of temp table.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> !columns temp

+------------+----------------+-------------+--------------+------------+------------+--------------+----------------+-----------------+-----------------+-----------+----------+-------------+----------------+-------------------+--------------------+-------------------+--------------+----------------+---------------+--------------+-------------------+--------------------+
| TABLE_CAT  |  TABLE_SCHEM   | TABLE_NAME  | COLUMN_NAME  | DATA_TYPE  | TYPE_NAME  | COLUMN_SIZE  | BUFFER_LENGTH  | DECIMAL_DIGITS  | NUM_PREC_RADIX  | NULLABLE  | REMARKS  | COLUMN_DEF  | SQL_DATA_TYPE  | SQL_DATETIME_SUB  | CHAR_OCTET_LENGTH  | ORDINAL_POSITION  | IS_NULLABLE  | SCOPE_CATALOG  | SCOPE_SCHEMA  | SCOPE_TABLE  | SOURCE_DATA_TYPE  | IS_AUTO_INCREMENT  |
+------------+----------------+-------------+--------------+------------+------------+--------------+----------------+-----------------+-----------------+-----------+----------+-------------+----------------+-------------------+--------------------+-------------------+--------------+----------------+---------------+--------------+-------------------+--------------------+
| NULL       | aledeuf        | temp        | col          | 12         | STRING     | 2147483647   | NULL           | NULL            | NULL            | 1         | NULL     | NULL        | NULL           | NULL              | NULL               | 1                 | YES          | NULL           | NULL          | NULL         | NULL              | NO                 |
| NULL       | apignerol      | temp        | col          | 12         | STRING     | 2147483647   | NULL           | NULL            | NULL            | 1         | NULL     | NULL        | NULL           | NULL              | NULL               | 1                 | YES          | NULL           | NULL          | NULL         | NULL              | NO                 |
| NULL       | vgonnot        | temp        | col          | 12         | STRING     | 2147483647   | NULL           | NULL            | NULL            | 1         | NULL     | NULL        | NULL           | NULL              | NULL               | 1                 | YES          | NULL           | NULL          | NULL         | NULL              | NO                 |
| NULL       | idelaronciere  | temp        | col          | 12         | STRING     | 2147483647   | NULL           | NULL            | NULL            | 1         | NULL     | NULL        | NULL           | NULL              | NULL               | 1                 | YES          | NULL           | NULL          | NULL         | NULL              | NO                 |
| NULL       | lboumriche     | temp        | col          | 12         | STRING     | 2147483647   | NULL           | NULL            | NULL            | 1         | NULL     | NULL        | NULL           | NULL              | NULL               | 1                 | YES          | NULL           | NULL          | NULL         | NULL              | NO                 |
+------------+----------------+-------------+--------------+------------+------------+--------------+----------------+-----------------+-----------------+-----------+----------+-------------+----------------+-------------------+--------------------+-------------------+--------------+----------------+---------------+--------------+-------------------+--------------------+
```

### Remove the table.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> drop table temp

. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201110115004_9cd7c55d-fe50-49a4-8ef2-1651bf5d262d): drop table temp
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20201110115004_9cd7c55d-fe50-49a4-8ef2-1651bf5d262d); Time taken: 0.014 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201110115004_9cd7c55d-fe50-49a4-8ef2-1651bf5d262d): drop table temp
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201110115004_9cd7c55d-fe50-49a4-8ef2-1651bf5d262d); Time taken: 0.149 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.18 seconds)
```

### Type !quit to exit the beeline shell.
```CMD
0: jdbc:hive2://hadoop-master01.efrei.online:> !quit

Closing: 0: jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/default;httpPath=cliservice;principal=hive/_HOST@EFREI.ONLINE;serviceDiscoveryMode=zooKeeper;ssl=true;transportMode=http;zooKeeperNamespace=hiveserver2
```



## 1.2 Create tables

### Create an external table called trees external.
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> create external table if not exists trees_external(Geopoint String, Arrondissement Integer, Genre String, Espece String, Famille String, Annee_plante Integer, Circonference Integer, Adresse String, Commune String, Variete String, Id Integer, Lieu String) Row format delimited fields terminated by ';' location 'hdfs://efrei/user/apignerol/input-trees' tblproperties ("skip.header.line.count" = "1");
```
```CMD
INFO  : Compiling command(queryId=hive_20201111101403_ecc3fcdf-7077-4ad6-bb91-ce6ac5b0a9c1): create external table if not exists trees_external(Geopoint String, Arrondissement Integer, Genre String, Espece String, Famille String, Annee_plante Integer, Circonference Integer, Adresse String, Commune String, Variete String, Id Integer, Lieu String) Row format delimited fields terminated by ';' location 'hdfs://efrei/user/apignerol/input-trees' tblproperties ("skip.header.line.count" = "1")
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20201111101403_ecc3fcdf-7077-4ad6-bb91-ce6ac5b0a9c1); Time taken: 0.018 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111101403_ecc3fcdf-7077-4ad6-bb91-ce6ac5b0a9c1): create external table if not exists trees_external(Geopoint String, Arrondissement Integer, Genre String, Espece String, Famille String, Annee_plante Integer, Circonference Integer, Adresse String, Commune String, Variete String, Id Integer, Lieu String) Row format delimited fields terminated by ';' location 'hdfs://efrei/user/apignerol/input-trees' tblproperties ("skip.header.line.count" = "1")
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201111101403_ecc3fcdf-7077-4ad6-bb91-ce6ac5b0a9c1); Time taken: 0.054 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.081 seconds)
```

### Create an internal table called trees internal.
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> create table if not exists trees_internal(Geopoint String, Arrondissement Integer, Genre String, Espece String, Famille String, Annee_plante Integer, Circonference Integer, Adresse String, Commune String, Variete String, Id Integer, Lieu String) Row format delimited fields terminated by ';' stored as orc;
```
```CMD
INFO  : Compiling command(queryId=hive_20201111101453_d8a5c676-0329-4635-a5b0-62ce91cd089f): create table if not exists trees_internal(Geopoint String, Arrondissement Integer, Genre String, Espece String, Famille String, Annee_plante Integer, Circonference Integer, Adresse String, Commune String, Variete String, Id Integer, Lieu String) Row format delimited fields terminated by ';' stored as orc
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20201111101453_d8a5c676-0329-4635-a5b0-62ce91cd089f); Time taken: 0.007 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111101453_d8a5c676-0329-4635-a5b0-62ce91cd089f): create table if not exists trees_internal(Geopoint String, Arrondissement Integer, Genre String, Espece String, Famille String, Annee_plante Integer, Circonference Integer, Adresse String, Commune String, Variete String, Id Integer, Lieu String) Row format delimited fields terminated by ';' stored as orc
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20201111101453_d8a5c676-0329-4635-a5b0-62ce91cd089f); Time taken: 0.04 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.058 seconds)
```

### Import data to the internal table using the external table.
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> insert overwrite table trees_internal select * from trees_external
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111101801_fd7bef2e-a7aa-4b9d-8fcb-9108cafa8fa1): insert overwrite table trees_internal select * from trees_external
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:trees_external.geopoint, type:string, comment:null), FieldSchema(name:trees_external.arrondissement, type:int, comment:null), FieldSchema(name:trees_external.genre, type:string, comment:null), FieldSchema(name:trees_external.espece, type:string, comment:null), FieldSchema(name:trees_external.famille, type:string, comment:null), FieldSchema(name:trees_external.annee_plante, type:int, comment:null), FieldSchema(name:trees_external.circonference, type:int, comment:null), FieldSchema(name:trees_external.adresse, type:string, comment:null), FieldSchema(name:trees_external.commune, type:string, comment:null), FieldSchema(name:trees_external.variete, type:string, comment:null), FieldSchema(name:trees_external.id, type:int, comment:null), FieldSchema(name:trees_external.lieu, type:string, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111101801_fd7bef2e-a7aa-4b9d-8fcb-9108cafa8fa1); Time taken: 0.158 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111101801_fd7bef2e-a7aa-4b9d-8fcb-9108cafa8fa1): insert overwrite table trees_internal select * from trees_external
INFO  : Query ID = hive_20201111101801_fd7bef2e-a7aa-4b9d-8fcb-9108cafa8fa1
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111101801_fd7bef2e-a7aa-4b9d-8fcb-9108cafa8fa1
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: insert overwrite table tree...trees_external (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3751)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 6.73 s
----------------------------------------------------------------------------------------------
INFO  : Starting task [Stage-2:DEPENDENCY_COLLECTION] in serial mode
INFO  : Starting task [Stage-0:MOVE] in serial mode
INFO  : Loading data to table apignerol.trees_internal from hdfs://efrei/warehouse/tablespace/external/hive/apignerol.db/trees_internal/.hive-staging_hive_2020-11-11_10-18-01_163_23949347183840428-142/-ext-10000
INFO  : Starting task [Stage-3:STATS] in serial mode
INFO  : Completed executing command(queryId=hive_20201111101801_fd7bef2e-a7aa-4b9d-8fcb-9108cafa8fa1); Time taken: 15.073 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (15.251 seconds)
```

### Verify that each table got the same lines count
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select count(*) from trees_external
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111102042_a7545ecd-883b-49e6-a6ff-a5a1c1df7ba3): select count(*) from trees_external
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:_c0, type:bigint, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111102042_a7545ecd-883b-49e6-a6ff-a5a1c1df7ba3); Time taken: 0.107 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111102042_a7545ecd-883b-49e6-a6ff-a5a1c1df7ba3): select count(*) from trees_external
INFO  : Query ID = hive_20201111102042_a7545ecd-883b-49e6-a6ff-a5a1c1df7ba3
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111102042_a7545ecd-883b-49e6-a6ff-a5a1c1df7ba3
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: select count(*) from trees_external (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3752)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 6.47 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111102042_a7545ecd-883b-49e6-a6ff-a5a1c1df7ba3); Time taken: 14.344 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+------+
| _c0  |
+------+
| 97   |
+------+
1 row selected (14.547 seconds)
```
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select count(*) from trees_internal
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111102109_ad55a97b-b00a-4c2f-a975-b42e4360be1a): select count(*) from trees_internal
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:_c0, type:bigint, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111102109_ad55a97b-b00a-4c2f-a975-b42e4360be1a); Time taken: 0.211 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111102109_ad55a97b-b00a-4c2f-a975-b42e4360be1a): select count(*) from trees_internal
INFO  : Query ID = hive_20201111102109_ad55a97b-b00a-4c2f-a975-b42e4360be1a
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111102109_ad55a97b-b00a-4c2f-a975-b42e4360be1a
INFO  : Session is already open
INFO  : Dag name: select count(*) from trees_internal (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3752)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 4.14 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111102109_ad55a97b-b00a-4c2f-a975-b42e4360be1a); Time taken: 4.818 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+------+
| _c0  |
+------+
| 97   |
+------+
1 row selected (5.068 seconds)
```



## 1.3 Create queries

### displays the list of district containing trees;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select distinct Arrondissement from trees_internal
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111102616_235c8e34-d1e9-47a2-a7ae-f5493c815bc6): select distinct Arrondissement from trees_internal
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:arrondissement, type:int, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111102616_235c8e34-d1e9-47a2-a7ae-f5493c815bc6); Time taken: 0.157 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111102616_235c8e34-d1e9-47a2-a7ae-f5493c815bc6): select distinct Arrondissement from trees_internal
INFO  : Query ID = hive_20201111102616_235c8e34-d1e9-47a2-a7ae-f5493c815bc6
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111102616_235c8e34-d1e9-47a2-a7ae-f5493c815bc6
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: select distinct Arrondissem...trees_internal (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3755)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 4.82 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111102616_235c8e34-d1e9-47a2-a7ae-f5493c815bc6); Time taken: 13.272 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------------+
| arrondissement  |
+-----------------+
| 3               |
| 4               |
| 5               |
| 6               |
| 7               |
| 8               |
| 9               |
| 11              |
| 12              |
| 13              |
| 14              |
| 15              |
| 16              |
| 17              |
| 18              |
| 19              |
| 20              |
+-----------------+
17 rows selected (13.547 seconds)
```

### displays the list of different species trees;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select distinct Genre from trees_internal
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111102759_6fcd0079-747e-4ffc-aec3-101c9e1ebade): select distinct Genre from trees_internal
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:genre, type:string, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111102759_6fcd0079-747e-4ffc-aec3-101c9e1ebade); Time taken: 0.1 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111102759_6fcd0079-747e-4ffc-aec3-101c9e1ebade): select distinct Genre from trees_internal
INFO  : Query ID = hive_20201111102759_6fcd0079-747e-4ffc-aec3-101c9e1ebade
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111102759_6fcd0079-747e-4ffc-aec3-101c9e1ebade
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: select distinct Genre from trees_internal (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3757)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 6.86 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111102759_6fcd0079-747e-4ffc-aec3-101c9e1ebade); Time taken: 14.838 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------------+
|      genre      |
+-----------------+
| Acer            |
| Aesculus        |
| Ailanthus       |
| Alnus           |
| Araucaria       |
| Broussonetia    |
| Calocedrus      |
| Catalpa         |
| Cedrus          |
| Celtis          |
| Corylus         |
| Davidia         |
| Diospyros       |
| Eucommia        |
| Fagus           |
| Fraxinus        |
| Ginkgo          |
| Gymnocladus     |
| Juglans         |
| Liriodendron    |
| Maclura         |
| Magnolia        |
| Paulownia       |
| Pinus           |
| Platanus        |
| Pterocarya      |
| Quercus         |
| Robinia         |
| Sequoia         |
| Sequoiadendron  |
| Styphnolobium   |
| Taxodium        |
| Taxus           |
| Tilia           |
| Ulmus           |
| Zelkova         |
+-----------------+
36 rows selected (15.035 seconds)
```

### the number of trees of each kind;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select Genre, Count(Genre) from trees_internal group by Genre
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111103722_6ef376c9-6ae3-4820-82a6-89b4d6f683b3): select Genre, Count(Genre) from trees_internal group by Genre
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:genre, type:string, comment:null), FieldSchema(name:_c1, type:bigint, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111103722_6ef376c9-6ae3-4820-82a6-89b4d6f683b3); Time taken: 0.204 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111103722_6ef376c9-6ae3-4820-82a6-89b4d6f683b3): select Genre, Count(Genre) from trees_internal group by Genre
INFO  : Query ID = hive_20201111103722_6ef376c9-6ae3-4820-82a6-89b4d6f683b3
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111103722_6ef376c9-6ae3-4820-82a6-89b4d6f683b3
INFO  : Session is already open
INFO  : Dag name: select Genre, Count(Genre) from tree...Genre (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3759)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 6.30 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111103722_6ef376c9-6ae3-4820-82a6-89b4d6f683b3); Time taken: 7.076 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------------+------+
|      genre      | _c1  |
+-----------------+------+
| Acer            | 3    |
| Aesculus        | 3    |
| Ailanthus       | 1    |
| Alnus           | 1    |
| Araucaria       | 1    |
| Broussonetia    | 1    |
| Calocedrus      | 1    |
| Catalpa         | 1    |
| Cedrus          | 4    |
| Celtis          | 1    |
| Corylus         | 3    |
| Davidia         | 1    |
| Diospyros       | 4    |
| Eucommia        | 1    |
| Fagus           | 8    |
| Fraxinus        | 1    |
| Ginkgo          | 5    |
| Gymnocladus     | 1    |
| Juglans         | 1    |
| Liriodendron    | 2    |
| Maclura         | 1    |
| Magnolia        | 1    |
| Paulownia       | 1    |
| Pinus           | 5    |
| Platanus        | 19   |
| Pterocarya      | 3    |
| Quercus         | 4    |
| Robinia         | 1    |
| Sequoia         | 1    |
| Sequoiadendron  | 5    |
| Styphnolobium   | 1    |
| Taxodium        | 3    |
| Taxus           | 2    |
| Tilia           | 1    |
| Ulmus           | 1    |
| Zelkova         | 4    |
+-----------------+------+
36 rows selected (7.368 seconds)
```

### calculates the height of the tallest tree of each kind;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select Genre, Max(Circonference) from trees_internal group by Genre
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111104329_9119e185-7088-466e-a449-a5979aacfa7f): select Genre, Max(Circonference) from trees_internal group by Genre
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:genre, type:string, comment:null), FieldSchema(name:_c1, type:int, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111104329_9119e185-7088-466e-a449-a5979aacfa7f); Time taken: 0.221 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111104329_9119e185-7088-466e-a449-a5979aacfa7f): select Genre, Max(Circonference) from trees_internal group by Genre
INFO  : Query ID = hive_20201111104329_9119e185-7088-466e-a449-a5979aacfa7f
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111104329_9119e185-7088-466e-a449-a5979aacfa7f
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: select Genre, Max(Circonference) fro...Genre (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3760)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 02/02  [==========================>>] 100%  ELAPSED TIME: 6.74 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111104329_9119e185-7088-466e-a449-a5979aacfa7f); Time taken: 14.774 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------------+------+
|      genre      | _c1  |
+-----------------+------+
| Acer            | 16   |
| Aesculus        | 30   |
| Ailanthus       | 35   |
| Alnus           | 16   |
| Araucaria       | 9    |
| Broussonetia    | 12   |
| Calocedrus      | 20   |
| Catalpa         | 15   |
| Cedrus          | 30   |
| Celtis          | 16   |
| Corylus         | 20   |
| Davidia         | 12   |
| Diospyros       | 14   |
| Eucommia        | 12   |
| Fagus           | 30   |
| Fraxinus        | 30   |
| Ginkgo          | 33   |
| Gymnocladus     | 10   |
| Juglans         | 28   |
| Liriodendron    | 35   |
| Maclura         | 13   |
| Magnolia        | 12   |
| Paulownia       | 20   |
| Pinus           | 30   |
| Platanus        | 45   |
| Pterocarya      | 30   |
| Quercus         | 31   |
| Robinia         | 11   |
| Sequoia         | 30   |
| Sequoiadendron  | 35   |
| Styphnolobium   | 10   |
| Taxodium        | 35   |
| Taxus           | 13   |
| Tilia           | 20   |
| Ulmus           | 15   |
| Zelkova         | 30   |
+-----------------+------+
36 rows selected (15.093 seconds)
```

### sort the trees height from smallest to largest;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select Genre, Circonference from trees_internal order by Circonference
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111104710_1e4ae6bc-2d7b-4409-adeb-d70151697b64): select Genre, Circonference from trees_internal order by Circonference
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:genre, type:string, comment:null), FieldSchema(name:circonference, type:int, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111104710_1e4ae6bc-2d7b-4409-adeb-d70151697b64); Time taken: 0.176 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111104710_1e4ae6bc-2d7b-4409-adeb-d70151697b64): select Genre, Circonference from trees_internal order by Circonference
INFO  : Query ID = hive_20201111104710_1e4ae6bc-2d7b-4409-adeb-d70151697b64
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111104710_1e4ae6bc-2d7b-4409-adeb-d70151697b64
INFO  : Session is already open
INFO  : Dag name: select Genre, Circonference ...Circonference (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3761)

INFO  : Completed executing command(queryId=hive_20201111104710_1e4ae6bc-2d7b-4409-adeb-d70151697b64); Time taken: 0.786 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------------+----------------+
|      genre      | circonference  |
+-----------------+----------------+
| Sequoiadendron  | NULL           |
| Fagus           | 2              |
| Taxus           | 5              |
| Cedrus          | 6              |
| Araucaria       | 9              |
| Quercus         | 10             |
| Styphnolobium   | 10             |
| Fagus           | 10             |
| Gymnocladus     | 10             |
| Pinus           | 10             |
| Robinia         | 11             |
| Magnolia        | 12             |
| Acer            | 12             |
| Diospyros       | 12             |
| Davidia         | 12             |
| Diospyros       | 12             |
| Eucommia        | 12             |
| Broussonetia    | 12             |
| Zelkova         | 12             |
| Taxus           | 13             |
| Maclura         | 13             |
| Diospyros       | 14             |
| Pinus           | 14             |
| Diospyros       | 14             |
| Acer            | 15             |
| Quercus         | 15             |
| Ulmus           | 15             |
| Fagus           | 15             |
| Catalpa         | 15             |
| Celtis          | 16             |
| Zelkova         | 16             |
| Alnus           | 16             |
| Acer            | 16             |
| Fagus           | 18             |
| Zelkova         | 18             |
| Ginkgo          | 18             |
| Aesculus        | 18             |
| Corylus         | 20             |
| Calocedrus      | 20             |
| Paulownia       | 20             |
| Fagus           | 20             |
| Platanus        | 20             |
| Corylus         | 20             |
| Corylus         | 20             |
| Platanus        | 20             |
| Sequoiadendron  | 20             |
| Taxodium        | 20             |
| Platanus        | 20             |
| Tilia           | 20             |
| Ginkgo          | 22             |
| Liriodendron    | 22             |
| Platanus        | 22             |
| Aesculus        | 22             |
| Pterocarya      | 22             |
| Fagus           | 23             |
| Pinus           | 25             |
| Platanus        | 25             |
| Ginkgo          | 25             |
| Ginkgo          | 25             |
| Platanus        | 25             |
| Cedrus          | 25             |
| Platanus        | 26             |
| Pterocarya      | 27             |
| Platanus        | 27             |
| Juglans         | 28             |
| Fagus           | 30             |
| Cedrus          | 30             |
| Fraxinus        | 30             |
| Cedrus          | 30             |
| Sequoiadendron  | 30             |
| Pterocarya      | 30             |
| Taxodium        | 30             |
| Pinus           | 30             |
| Quercus         | 30             |
| Platanus        | 30             |
| Sequoiadendron  | 30             |
| Pinus           | 30             |
| Zelkova         | 30             |
| Sequoia         | 30             |
| Aesculus        | 30             |
| Platanus        | 30             |
| Fagus           | 30             |
| Quercus         | 31             |
| Platanus        | 31             |
| Platanus        | 32             |
| Ginkgo          | 33             |
| Platanus        | 34             |
| Ailanthus       | 35             |
| Platanus        | 35             |
| Taxodium        | 35             |
| Sequoiadendron  | 35             |
| Liriodendron    | 35             |
| Platanus        | 40             |
| Platanus        | 40             |
| Platanus        | 40             |
| Platanus        | 42             |
| Platanus        | 45             |
+-----------------+----------------+
97 rows selected (1.014 seconds)
```

### displays the district where the oldest tree is;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select Genre, Annee_plante from trees_internal where Annee_plante = (select Min(Annee_plante) from trees_internal)
```
```CMD
. . . . . . . . . . . . . . . . . . . . . . .> INFO  : Compiling command(queryId=hive_20201111105631_2644546d-1e36-4e46-a010-8bf664cee240): select Genre, Annee_plante from trees_internal where Annee_plante = (select Min(Annee_plante) from trees_internal)
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:genre, type:string, comment:null), FieldSchema(name:annee_plante, type:int, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111105631_2644546d-1e36-4e46-a010-8bf664cee240); Time taken: 0.279 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111105631_2644546d-1e36-4e46-a010-8bf664cee240): select Genre, Annee_plante from trees_internal where Annee_plante = (select Min(Annee_plante) from trees_internal)
INFO  : Query ID = hive_20201111105631_2644546d-1e36-4e46-a010-8bf664cee240
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111105631_2644546d-1e36-4e46-a010-8bf664cee240
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: select Genre, Annee_plante...trees_internal) (Stage-1)
INFO  : Setting tez.task.scale.memory.reserve-fraction to 0.30000001192092896
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3767)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 2 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 3 ...... container     SUCCEEDED      1          1        0        0       0       0
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 03/03  [==========================>>] 100%  ELAPSED TIME: 7.32 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111105631_2644546d-1e36-4e46-a010-8bf664cee240); Time taken: 15.469 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+----------+---------------+
|  genre   | annee_plante  |
+----------+---------------+
| Robinia  | 1601          |
+----------+---------------+
1 row selected (15.892 seconds)
```

### displays the district that contains the most trees;
```SQL
0: jdbc:hive2://hadoop-master01.efrei.online:> select t.Arrondissement as Arrondissement from (select Arrondissement, Count(*) as nbArbre from trees_internal group by Arrondissement order by nbArbre desc limit 1) t;
```
```CMD
INFO  : Compiling command(queryId=hive_20201111135226_c053a0fb-6577-4080-99e8-b165325aa0b6): select t.Arrondissement as Arrondissement from (select Arrondissement, Count(*) as nbArbre from trees_internal group by Arrondissement order by nbArbre desc limit 1) t
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:arrondissement, type:int, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20201111135226_c053a0fb-6577-4080-99e8-b165325aa0b6); Time taken: 0.191 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20201111135226_c053a0fb-6577-4080-99e8-b165325aa0b6): select t.Arrondissement as Arrondissement from (select Arrondissement, Count(*) as nbArbre from trees_internal group by Arrondissement order by nbArbre desc limit 1) t
INFO  : Query ID = hive_20201111135226_c053a0fb-6577-4080-99e8-b165325aa0b6
INFO  : Total jobs = 1
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Subscribed to counters: [] for queryId: hive_20201111135226_c053a0fb-6577-4080-99e8-b165325aa0b6
INFO  : Tez session hasn't been created yet. Opening session
INFO  : Dag name: select t.Arrondissement as Arrondissemen...t (Stage-1)
INFO  : Status: Running (Executing on YARN cluster with App id application_1603290159664_3827)

----------------------------------------------------------------------------------------------
        VERTICES      MODE        STATUS  TOTAL  COMPLETED  RUNNING  PENDING  FAILED  KILLED
----------------------------------------------------------------------------------------------
Map 1 .......... container     SUCCEEDED      1          1        0        0       0       0
Reducer 2 ...... container     SUCCEEDED      1          1        0        0       0       0
Reducer 3 ...... container     SUCCEEDED      1          1        0        0       0       0
----------------------------------------------------------------------------------------------
VERTICES: 03/03  [==========================>>] 100%  ELAPSED TIME: 7.46 s
----------------------------------------------------------------------------------------------
INFO  : Completed executing command(queryId=hive_20201111135226_c053a0fb-6577-4080-99e8-b165325aa0b6); Time taken: 15.586 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------------+
| arrondissement  |
+-----------------+
| 16              |
+-----------------+
1 row selected (15.9 seconds)
```