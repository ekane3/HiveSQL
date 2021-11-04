# Apache Hive
## *Emile .E. EKANE*
## *04/11/2021*
## *Contact Info: [ekane3/github/io](http://ekane3.gi)*
<br><br>

# 1. Hive Beeline Client
Here, we will verify the connection to Hive using Beeline client.
## 1.1 Create a Connection to Beeline Client
- Let's connect to our Hive Server using Beeline client.
```powershell
Using username "emile.ekane-ekane".
Keyboard-interactive authentication prompts from server:
End of keyboard-interactive prompts from server
Last login: Thu Nov  4 13:00:33 2021 from nat-in-drelab.groupe-efrei.fr
[emile.ekane-ekane@hadoop-edge01 ~]$ kinit
Password for emile.ekane-ekane@EFREI.ONLINE:
[emile.ekane-ekane@hadoop-edge01 ~]$ beeline
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/usr/odp/1.0.3.0-223/hive/lib/log4j-slf4j-impl-2.10.0.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/usr/odp/1.0.3.0-223/hadoop/lib/slf4j-log4j12-1.7.25.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [org.apache.logging.slf4j.Log4jLoggerFactory]
Connecting to jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/default;httpPath=cliservice;principal=hive/_HOST@EFREI.ONLINE;serviceDiscoveryMode=zooKeeper;ssl=true;transportMode=http;zooKeeperNamespace=hiveserver2
21/11/04 13:04:25 [main]: INFO jdbc.HiveConnection: Connected to hadoop-master02.efrei.online:10001
Connected to: Apache Hive (version 3.1.2.1.0.3.0-223)
Driver: Hive JDBC (version 3.1.2.1.0.3.0-223)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 3.1.2.1.0.3.0-223 by Apache Hive
0: jdbc:hive2://hadoop-master01.efrei.online:> !connect jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=hiveserver2
Connecting to jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=hiveserver2
Enter username for jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/:
Enter password for jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/:
21/11/04 13:08:08 [main]: INFO jdbc.HiveConnection: Connected to hadoop-master01.efrei.online:10001
Connected to: Apache Hive (version 3.1.2.1.0.3.0-223)
Driver: Hive JDBC (version 3.1.2.1.0.3.0-223)
Transaction isolation: TRANSACTION_REPEATABLE_READ
1: jdbc:hive2://hadoop-master01.efrei.online:>

```	
-   Help command to list beeline commands
```powershell	
0: jdbc:hive2://hadoop-master01.efrei.online:> help
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
- Which command allows you to view the jdbc connection used to connect to HiveServer2 

```powershell
!list
```	
- List all databases
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> SHOW DATABASES;
INFO  : Compiling command(queryId=hive_20211104132001_cc4f7985-199a-4f84-a3d7-0970ddab72e8): SHOW DATABASES
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20211104132001_cc4f7985-199a-4f84-a3d7-0970ddab72e8); Time taken: 0.101 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104132001_cc4f7985-199a-4f84-a3d7-0970ddab72e8): SHOW DATABASES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104132001_cc4f7985-199a-4f84-a3d7-0970ddab72e8); Time taken: 0.008 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-------------------------------+
|         database_name         |
+-------------------------------+
| a_aney                        |
| a_chevron                     |
| a_ngau                        |
| a_poloubinski                 |
| a_tonlop                      |
| adrouineau_areino             |
| aflorentz                     |
| ajond                         |
| alan                          |
| alemasne                      |
| amessika                      |
| ananda                        |
| anas                          |
| anas_m                        |
| armel                         |
| arnaud_parmentier             |
| arouhi                        |
| arthy_kandiah                 |
| avacchianimarcuzzo            |
| avellard                      |
| b_gabrieleff                  |
| balthazar_r                   |
| baud                          |
| baudouindlv                   |
| bcimetiere                    |
| bclaudic                      |
| bcourtois                     |
| benjamin                      |
| berenice                      |
| bfoin                         |
| bil_bendaoud                  |
| bintou                        |
| bnguyen                       |
| cedric_kabore                 |
| cgrandclaude                  |
| charlesptacek                 |
| cjdidi                        |
| cmauvezin                     |
| cvenet                        |
| default                       |
| droguet                       |
| e_bernard                     |
| e_diez                        |
| e_guedj                       |
| e_joliman                     |
| e_yimene_kaze                 |
| ebitton                       |
| emp                           |
| eya_database                  |
| eya_gheyouche                 |
| f_montiel                     |
| fbakhti                       |
| felixpillot                   |
| g_ngueyap                     |
| godard                        |
| grace                         |
| grace_alima                   |
| grace_alimata_sana            |
| grace_sana                    |
| graiess                       |
| gudronlauret                  |
| gugu                          |
| gugulpb                       |
| h_feruglio                    |
| halvarez                      |
| hdubouillon                   |
| hive1                         |
| hugo_pagny                    |
| hugokauffman                  |
| hugues_roland                 |
| i_aderdour                    |
| i_jelila                      |
| ilyass_bourkaik               |
| imeira                        |
| ines_benabed                  |
| information_schema            |
| j_ditsouga_perera             |
| j_mirgaine                    |
| jbenayad                      |
| jcharbonnaud                  |
| jcrecel                       |
| jehl                          |
| jingtao_qu                    |
| karim                         |
| karim_malle                   |
| kevin_ngo                     |
| kgwet                         |
| khauv                         |
| ksritharan                    |
| ktan                          |
| ktazi                         |
| l_barazer                     |
| l_etzol                       |
| l_ferrand                     |
| l_maiz                        |
| l_manceau                     |
| lanthoine                     |
| lgaillard                     |
| llecomte                      |
| lrodriguez                    |
+-------------------------------+
|         database_name         |
+-------------------------------+
| lucas_maiz                    |
| lucie_bottin                  |
| m_abatti                      |
| m_iloo_liandja                |
| ma_baseismail                 |
| maboualam                     |
| mame                          |
| mame_aicha_dieye              |
| manuella                      |
| marieblein                    |
| maximesennechael              |
| mbourabah                     |
| mdufau                        |
| melyachkouri                  |
| mhanania                      |
| mhatoum                       |
| moukaci                       |
| ncailleux                     |
| ncolard                       |
| ne_oubenami                   |
| ninon                         |
| nourris                       |
| nruiz                         |
| ntharmaseelan                 |
| nzebair                       |
| p_huang                       |
| p_ngoufack                    |
| pbertrand                     |
| pho                           |
| pierre_aymerick_dzou_ekassi   |
| pmeignan                      |
| q_nicot                       |
| r_hetet                       |
| r_ouedraogo                   |
| rania_elha                    |
| rbocchini                     |
| rbouderghouma                 |
| rbourourou                    |
| revillon                      |
| rhetet                        |
| rlancelot                     |
| rlegrand                      |
| rleveille_nizerolle           |
| robinlazarus                  |
| romainw                       |
| s_ano                         |
| s_benabidallah                |
| s_touret                      |
| sarnaud                       |
| sbrisard                      |
| schen                         |
| sghlouci                      |
| skeutcha                      |
| spiquet                       |
| spruvot                       |
| svassent                      |
| sys                           |
| t_casini                      |
| t_goujon                      |
| temp                          |
| thomas_nrcl                   |
| tpcds_bin_partitioned_orc_15  |
| tpcds_text_15                 |
| tvenec                        |
| v_richard                     |
| vaihau_williamu               |
| vanelle_domo                  |
| vbonneff                      |
| victorine                     |
| vincent_ly                    |
| vincent_tran                  |
| wang_ye                       |
| wangye                        |
| wendy                         |
| wilfried_ponnou               |
| wilmei                        |
| y_jendoubi                    |
| yang_chen                     |
| yingda                        |
| ymaassouli                    |
| ymeli                         |
+-------------------------------+
181 rows selected (0.249 seconds)

```

- If not exist create database using your username 
```powershell
1: jdbc:hive2://hadoop-master01.efrei.online:> CREATE DATABASE IF NOT EXISTS emile_ekane_ekane;
INFO  : Compiling command(queryId=hive_20211104132705_a4967ceb-710a-40ee-b431-b785eefed6f1): CREATE DATABASE IF NOT EXISTS emile_ekane_ekane
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20211104132705_a4967ceb-710a-40ee-b431-b785eefed6f1); Time taken: 0.013 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104132705_a4967ceb-710a-40ee-b431-b785eefed6f1): CREATE DATABASE IF NOT EXISTS emile_ekane_ekane
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104132705_a4967ceb-710a-40ee-b431-b785eefed6f1); Time taken: 0.028 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.05 seconds)

```	
- Use  your database
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> USE emile_ekane_ekane;
INFO  : Compiling command(queryId=hive_20211104132853_8cb63b77-23f8-4ef3-be95-e33f9d1355b1): USE emile_ekane_ekane
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20211104132853_8cb63b77-23f8-4ef3-be95-e33f9d1355b1); Time taken: 0.03 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104132853_8cb63b77-23f8-4ef3-be95-e33f9d1355b1): USE emile_ekane_ekane
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104132853_8cb63b77-23f8-4ef3-be95-e33f9d1355b1); Time taken: 0.033 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.079 seconds)

```	
- List all tables
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20211104133016_84d820c6-8b1b-43b7-8453-0585d5b1e900): SHOW TABLES
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20211104133016_84d820c6-8b1b-43b7-8453-0585d5b1e900); Time taken: 0.046 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104133016_84d820c6-8b1b-43b7-8453-0585d5b1e900): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104133016_84d820c6-8b1b-43b7-8453-0585d5b1e900); Time taken: 0.01 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+-----------+
| tab_name  |
+-----------+
+-----------+
No rows selected (0.08 seconds)

```	
- Create table called temp with a column called col of String type
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> CREATE TABLE temp(col String);
INFO  : Compiling command(queryId=hive_20211104133504_42af308b-9cdb-4f0b-988b-7273574eda2f): CREATE TABLE temp(col String)
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20211104133504_42af308b-9cdb-4f0b-988b-7273574eda2f); Time taken: 0.021 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104133504_42af308b-9cdb-4f0b-988b-7273574eda2f): CREATE TABLE temp(col String)
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104133504_42af308b-9cdb-4f0b-988b-7273574eda2f); Time taken: 0.027 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.065 seconds)

```	
- Remove the table
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> DROP TABLE temp;
INFO  : Compiling command(queryId=hive_20211104133614_bfbfdaf5-d6b6-453f-95dd-3ae19bd92827): DROP TABLE temp
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20211104133614_bfbfdaf5-d6b6-453f-95dd-3ae19bd92827); Time taken: 0.133 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104133614_bfbfdaf5-d6b6-453f-95dd-3ae19bd92827): DROP TABLE temp
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104133614_bfbfdaf5-d6b6-453f-95dd-3ae19bd92827); Time taken: 0.082 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.234 seconds)

```	
- Type !quit to exit the beeline shell
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> !quit
Closing: 1: jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=hiveserver2
Closing: 0: jdbc:hive2://hadoop-master01.efrei.online:2181,hadoop-master02.efrei.online:2181,hadoop-master03.efrei.online:2181/default;httpPath=cliservice;principal=hive/_HOST@EFREI.ONLINE;serviceDiscoveryMode=zooKeeper;ssl=true;transportMode=http;zooKeeperNamespace=hiveserver2
[emile.ekane-ekane@hadoop-edge01 ~]$

```	

<br><br>

## 1.2 Create tables
You are going to write some Hive SQL queries on the remarkable trees of Paris using this [dataset](https://github.com/makayel/hadoop-examples-mapreduce/blob/main/src/test/resources/data/trees.csv). If you got issues with TEZ, you must use the MapReduce engine for Hive SET hive.execution.engine=mr;

- Create an external table called trees_external.
```powershell	
1: jdbc:hive2://hadoop-master01.efrei.online:> CREATE EXTERNAL TABLE trees_external (
. . . . . . . . . . . . . . . . . . . . . . .> GEOPOINT STRING,
. . . . . . . . . . . . . . . . . . . . . . .> ARRONDISSEMENT INT,
. . . . . . . . . . . . . . . . . . . . . . .> GENRE STRING,
. . . . . . . . . . . . . . . . . . . . . . .> ESPECE STRING,
. . . . . . . . . . . . . . . . . . . . . . .> FAMILLE STRING,
. . . . . . . . . . . . . . . . . . . . . . .> ANNEE_PLANTATION DATE,
. . . . . . . . . . . . . . . . . . . . . . .> HAUTEUR FLOAT,
. . . . . . . . . . . . . . . . . . . . . . .> CIRCONFERENCE FLOAT,
. . . . . . . . . . . . . . . . . . . . . . .> ADRESSE STRING,
. . . . . . . . . . . . . . . . . . . . . . .> NOM_COMMUNE STRING,
. . . . . . . . . . . . . . . . . . . . . . .> VARIETE STRING,
. . . . . . . . . . . . . . . . . . . . . . .> OBJECTID INT,
. . . . . . . . . . . . . . . . . . . . . . .> NOM_EV STRING
. . . . . . . . . . . . . . . . . . . . . . .> )
. . . . . . . . . . . . . . . . . . . . . . .> ROW FORMAT DELIMITED
. . . . . . . . . . . . . . . . . . . . . . .> FIELDS TERMINATED BY ';'
. . . . . . . . . . . . . . . . . . . . . . .> LOCATION '/user/emile.ekane-ekane/treesdir';
INFO  : Compiling command(queryId=hive_20211104144546_ca07512a-cad7-48a2-9dd3-ebc658a8ca90): CREATE EXTERNAL TABLE trees_external (
GEOPOINT STRING,
ARRONDISSEMENT INT,
GENRE STRING,
ESPECE STRING,
FAMILLE STRING,
ANNEE_PLANTATION DATE,
HAUTEUR FLOAT,
CIRCONFERENCE FLOAT,
ADRESSE STRING,
NOM_COMMUNE STRING,
VARIETE STRING,
OBJECTID INT,
NOM_EV STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ';'
LOCATION '/user/emile.ekane-ekane/treesdir'
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20211104144546_ca07512a-cad7-48a2-9dd3-ebc658a8ca90); Time taken: 0.072 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104144546_ca07512a-cad7-48a2-9dd3-ebc658a8ca90): CREATE TABLE trees_external (
GEOPOINT STRING,
ARRONDISSEMENT INT,
GENRE STRING,
ESPECE STRING,
FAMILLE STRING,
ANNEE_PLANTATION DATE,
HAUTEUR FLOAT,
CIRCONFERENCE FLOAT,
ADRESSE STRING,
NOM_COMMUNE STRING,
VARIETE STRING,
OBJECTID INT,
NOM_EV STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ';'
LOCATION '/user/emile.ekane-ekane/treesdir'
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20211104144546_ca07512a-cad7-48a2-9dd3-ebc658a8ca90); Time taken: 0.083 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
No rows affected (0.173 seconds)


#To create trees_internal table, you must use the following command:
CREATE TABLE trees_internal (  
GEOPOINT STRING,  
ARRONDISSEMENT INT,  
GENRE STRING,  
ESPECE STRING,  
FAMILLE STRING,  
ANNEE_PLANTATION DATE,  
HAUTEUR FLOAT,
CIRCONFERENCE FLOAT,   
ADRESSE STRING,
NOM_COMMUNE STRING,       
VARIETE STRING,
OBJECTID INT,  
NOM_EV STRING   
) ;
```	

- Import data to the internal table using the external table.
```powershell	
 INSERT OVERWRITE TABLE trees_internal SELECT * FROM trees_external;
```
- Verify that each table got the same lines count.
```powershell	
SELECT * FROM trees_external;
SELECT * FROM trees_internal;
```
With these commands, you can see that the two tables have the same number of lines.
Results:
```powershell
1: jdbc:hive2://hadoop-master01.efrei.online:> select count(*) from trees_internal;
INFO  : Compiling command(queryId=hive_20211104145021_0c648086-c3fb-4c5c-8aab-77a72c15ff81): select count(*) from trees_internal
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Semantic Analysis Completed (retrial = false)
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:_c0, type:bigint, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20211104145021_0c648086-c3fb-4c5c-8aab-77a72c15ff81); Time taken: 0.402 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20211104145021_0c648086-c3fb-4c5c-8aab-77a72c15ff81): select count(*) from trees_internal
INFO  : Completed executing command(queryId=hive_20211104145021_0c648086-c3fb-4c5c-8aab-77a72c15ff81); Time taken: 0.003 seconds
INFO  : OK
INFO  : Concurrency mode is disabled, not creating a lock manager
+------+
| _c0  |
+------+
| 97   |
+------+

```	

<br><br>

## 1.3 Create queries
In this part, you are going to do the same queries as MapReduce ones using the
internal table created before. You will create queries that:

- displays the list of district containing trees;
```powershell	
SELECT DISTINCT ARRONDISSEMENT FROM trees_internal;

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
17 rows selected (30.972 seconds)

```
- displays the list of different species trees;
```powershell	
SELECT ESPECE FROM trees_internal GROUP BY ESPECE;

+-----------------+
|     espece      |
+-----------------+
| araucana        |
| atlantica       |
| australis       |
| baccata         |
| bignonioides    |
| biloba          |
| bungeana        |
| cappadocicum    |
| carpinifolia    |
| colurna         |
| coulteri        |
| decurrens       |
| dioicus         |
| distichum       |
| excelsior       |
| fraxinifolia    |
| giganteum       |
| giraldii        |
| glutinosa       |
| grandiflora     |
| hippocastanum   |
| ilex            |
| involucrata     |
| japonicum       |
| kaki            |
| libanii         |
| monspessulanum  |
| nigra           |
| nigra laricio   |
| opalus          |
| orientalis      |
| papyrifera      |
| petraea         |
| pomifera        |
| pseudoacacia    |
| sempervirens    |
| serrata         |
| stenoptera      |
| suber           |
| sylvatica       |
| tomentosa       |
| tulipifera      |
| ulmoides        |
| virginiana      |
| x acerifolia    |
+-----------------+
45 rows selected (28.272 seconds)


```
- the number of trees of each kind;
```powershell	
SELECT GENRE, COUNT(*) AS NB_TREES FROM trees_internal GROUP BY GENRE;

+-----------------+-----------+
|      genre      | nb_trees  |
+-----------------+-----------+
| Acer            | 3         |
| Aesculus        | 3         |
| Ailanthus       | 1         |
| Alnus           | 1         |
| Araucaria       | 1         |
| Broussonetia    | 1         |
| Calocedrus      | 1         |
| Catalpa         | 1         |
| Cedrus          | 4         |
| Celtis          | 1         |
| Corylus         | 3         |
| Davidia         | 1         |
| Diospyros       | 4         |
| Eucommia        | 1         |
| Fagus           | 8         |
| Fraxinus        | 1         |
| Ginkgo          | 5         |
| Gymnocladus     | 1         |
| Juglans         | 1         |
| Liriodendron    | 2         |
| Maclura         | 1         |
| Magnolia        | 1         |
| Paulownia       | 1         |
| Pinus           | 5         |
| Platanus        | 19        |
| Pterocarya      | 3         |
| Quercus         | 4         |
| Robinia         | 1         |
| Sequoia         | 1         |
| Sequoiadendron  | 5         |
| Styphnolobium   | 1         |
| Taxodium        | 3         |
| Taxus           | 2         |
| Tilia           | 1         |
| Ulmus           | 1         |
| Zelkova         | 4         |
+-----------------+-----------+
36 rows selected (26.668 seconds)


```
- calculates the height of the tallest tree of each kind;
```powershell	
SELECT GENRE, MAX(HAUTEUR) AS HEIGHT FROM trees_internal GROUP BY GENRE;

+-----------------+---------+
|      genre      | height  |
+-----------------+---------+
| Acer            | 16.0    |
| Aesculus        | 30.0    |
| Ailanthus       | 35.0    |
| Alnus           | 16.0    |
| Araucaria       | 9.0     |
| Broussonetia    | 12.0    |
| Calocedrus      | 20.0    |
| Catalpa         | 15.0    |
| Cedrus          | 30.0    |
| Celtis          | 16.0    |
| Corylus         | 20.0    |
| Davidia         | 12.0    |
| Diospyros       | 14.0    |
| Eucommia        | 12.0    |
| Fagus           | 30.0    |
| Fraxinus        | 30.0    |
| Ginkgo          | 33.0    |
| Gymnocladus     | 10.0    |
| Juglans         | 28.0    |
| Liriodendron    | 35.0    |
| Maclura         | 13.0    |
| Magnolia        | 12.0    |
| Paulownia       | 20.0    |
| Pinus           | 30.0    |
| Platanus        | 45.0    |
| Pterocarya      | 30.0    |
| Quercus         | 31.0    |
| Robinia         | 11.0    |
| Sequoia         | 30.0    |
| Sequoiadendron  | 35.0    |
| Styphnolobium   | 10.0    |
| Taxodium        | 35.0    |
| Taxus           | 13.0    |
| Tilia           | 20.0    |
| Ulmus           | 15.0    |
| Zelkova         | 30.0    |
+-----------------+---------+
36 rows selected (27.065 seconds)

```
- sort the trees height from smallest to largest;
```powershell	
SELECT ARRONDISSEMENT,FAMILLE,NOM_COMMUNE,CIRCONFERENCE FROM trees_internal ORDER BY CIRCONFERENCE ASC;

+-----------------+----------------+----------------------------+----------------+
| arrondissement  |    famille     |        nom_commune         | circonference  |
+-----------------+----------------+----------------------------+----------------+
| 12              | Ebenaceae      | Plaqueminier de Virginie   | NULL           |
| 16              | Taxodiaceae    | Séquoia géant              | NULL           |
| 16              | Magnoliaceae   | Magnolia à grandes fleurs  | NULL           |
| 7               | Moraceae       | Oranger des Osages         | NULL           |
| 12              | Fagaceae       | Chêne vert                 | NULL           |
| 12              | Pinaceae       | Pin Napoléon               | 50.0           |
| 5               | Fagaceae       | Faux de Verzy              | 72.0           |
| 16              | Cornaceae      | Arbre aux pochettes        | 120.0          |
| 12              | Taxaceae       | If commun                  | 140.0          |
| 16              | Araucariaceae  | Désespoir du singe         | 140.0          |
| 16              | Ebenaceae      | Kaki                       | 145.0          |
| 12              | Sapindaceae    | Erable d'Italie            | 160.0          |
| 12              | Ebenaceae      | Kaki                       | 160.0          |
| 16              | Fabaceae       | Chicot du Canada           | 162.0          |
| 12              | Ebenaceae      | Plaqueminier de Virginie   | 180.0          |
| 16              | Fagaceae       | Chêne liège                | 180.0          |
| 4               | Ulmaceae       | Orme champêtre             | 180.0          |
| 7               | Eucomiaceae    | Arbre à gutta-percha       | 190.0          |
| 16              | Moraceae       | Murier à papier            | 190.0          |
| 16              | Pinaceae       | Cèdre bleu de l'Atlas ple  | 195.0          |
| 8               | Cupressaceae   | Cèdre à encens             | 195.0          |
| 16              | Fagaceae       | Hêtre pleureur             | 200.0          |
| 12              | Magnoliaceae   | Tulipier de Virginie       | 205.0          |
| 19              | Malvaceae      | Tilleul argenté            | 205.0          |
| 3               | Betulaceae     | Noisetier de Byzance       | 210.0          |
| 16              | Ginkgoaceae    | Arbre aux quarante écus    | 215.0          |
| 15              | Betulaceae     | Aulne glutineux            | 220.0          |
| 20              | Sapindacaees   | Erable de Montpellier      | 225.0          |
| 12              | Pinaceae       | Pin aux grands cônes       | 225.0          |
| 19              | Ginkgoaceae    | Arbre aux quarante écus    | 230.0          |
| 16              | Fagaceae       | Hêtre pleureur             | 230.0          |
| 16              | Taxaceae       | If commun                  | 235.0          |
| 16              | Pinaceae       | Pin de Corse               | 240.0          |
| 12              | Ulmaceae       | Zelkova du Japon           | 240.0          |
| 11              | Betulaceae     | Noisetier de Byzance       | 245.0          |
| 12              | Ulmaceae       | Faux orme de Sibérie       | 245.0          |
| 12              | Pinaceae       | Pin noir                   | 248.0          |
| 16              | Pinaceae       | Pin noir                   | 250.0          |
| 12              | Ginkgoaceae    | Arbre aux quarante écus    | 255.0          |
| 16              | Ulmaceae       | Faux orme de Sibérie       | 260.0          |
| 6               | Bignoniaceae   | Catalpa commun             | 260.0          |
| 16              | Betulaceae     | Noisetier de Byzance       | 260.0          |
| 12              | Taxodiaceae    | Cyprés chauve              | 270.0          |
| 12              | Sapindaceae    | Erable de Cappadoce        | 280.0          |
| 8               | Ginkgoaceae    | Arbre aux quarante écus    | 283.0          |
| 16              | Taxodiaceae    | Cyprés chauve              | 290.0          |
| 12              | Cannabaceae    | Micocoulier de Provence    | 295.0          |
| 16              | Fagaceae       | Hêtre pourpre              | 300.0          |
| 12              | Magnoliaceae   | Tulipier de Virginie       | 305.0          |
| 8               | Taxodiaceae    | Séquoia géant              | 320.0          |
| 9               | Juglandaceae   | Pérocarya du Caucase       | 330.0          |
| 19              | Fabaceae       | Sophora du Japon           | 335.0          |
| 14              | Taxodiaceae    | Séquoia sempervirent       | 335.0          |
| 16              | Platanaceae    | Platane d'Orient           | 340.0          |
| 20              | Sapindaceae    | Marronnier d'Inde          | 345.0          |
| 16              | Taxodiaceae    | Cyprés chauve              | 350.0          |
| 13              | Pinaceae       | Cèdre bleu de l'Atlas      | 350.0          |
| 13              | Sapindaceae    | Marronnier d'Inde          | 355.0          |
| 19              | Oleaceae       | Frêne commun               | 365.0          |
| 14              | Fagaceae       | Hêtre pourpre              | 370.0          |
| 12              | Fagaceae       | Hêtre pourpre              | 370.0          |
| 16              | Platanaceae    | Platane d'Orient           | 375.0          |
| 5               | Fabaceae       | Robinier faux-acacia       | 385.0          |
| 16              | Ginkgoaceae    | Arbre aux quarante écus    | 395.0          |
| 16              | Ulmaceae       | Faux orme de Sibérie       | 395.0          |
| 20              | Platanaceae    | Platane commun             | 395.0          |
| 16              | Juglandaceae   | Pérocarya du Caucase       | 400.0          |
| 12              | Platanaceae    | Platane commun             | 405.0          |
| 12              | Platanaceae    | Platane commun             | 405.0          |
| 16              | Paulowniaceae  | Paulownia                  | 420.0          |
| 12              | Fagaceae       | Chêne rouvre               | 430.0          |
| 12              | Pinaceae       | Cèdre du Liban             | 440.0          |
| 12              | Fagaceae       | Chêne rouve                | 450.0          |
| 16              | Pinaceae       | Cèdre du Liban             | 460.0          |
| 16              | Simaroubaceae  | Ailanthe                   | 460.0          |
| 18              | Platanaceae    | Platane d'Orient           | 470.0          |
| 19              | Taxodiaceae    | Séquoia géant              | 470.0          |
| 12              | Platanaceae    | Platane d'Orient           | 475.0          |
| 16              | Platanaceae    | Platane commun             | 480.0          |
| 8               | Platanaceae    | Platane d'Orient           | 480.0          |
| 16              | Taxodiaceae    | Séquoia géant              | 490.0          |
| 12              | Platanaceae    | Platane commun             | 490.0          |
| 16              | Sapindaceae    | Marronnier d'Inde          | 505.0          |
| 12              | Platanaceae    | Platane commun             | 510.0          |
| 16              | Platanaceae    | Platane commun             | 520.0          |
| 16              | Platanaceae    | Platane commun             | 525.0          |
| 16              | Juglandaceae   | Ptérocarya de Chine        | 530.0          |
| 12              | Fagaceae       | Hêtre pleureur             | 530.0          |
| 16              | Fagaceae       | Hêtre pourpre              | 558.0          |
| 12              | Juglandaceae   | Noyer noir                 | 570.0          |
| 12              | Platanaceae    | Platane commun             | 570.0          |
| 14              | Platanaceae    | Platane commun             | 580.0          |
| 17              | Platanaceae    | Platane commun             | 595.0          |
| 16              | Taxodiaceae    | Séquoia géant              | 655.0          |
| 19              | Platanaceae    | Platane d'Orient           | 670.0          |
| 8               | Platanaceae    | Platane d'Orient           | 700.0          |
| 7               | Platanaceae    | Platane d'Orient           | 700.0          |
+-----------------+----------------+----------------------------+----------------+
97 rows selected (31.633 seconds)

```
- displays the district where the oldest tree is;
```powershell	
SELECT ARRONDISSEMENT,ANNEE_PLANTATION FROM trees_internal ORDER BY ANNEE_PLANTATION ASC LIMIT 1;

```
- displays the district that contains the most trees;

```powershell	
SELECT ARRONDISSEMENT,COUNT(*) AS NB FROM trees_internal GROUP BY ARRONDISSEMENT ORDER BY COUNT(*) DESC LIMIT 1;

+-----------------+-----+
| arrondissement  | nb  |
+-----------------+-----+
| 16              | 36  |
+-----------------+-----+
1 row selected (64.455 seconds)


```
