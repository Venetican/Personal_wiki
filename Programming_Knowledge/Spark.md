# Spark
-> process data in real-time across various clusters of computers using simple programming constructs

## Hadoop vs Spark
-> Processing data using MapReduce is slow and is done not in-memory, Spark do it in memory
-> Hadoop only batch processing of data <-> Spark performs both, batch and real-time processing
-> Hadoop supports kerberos authentication, which is difficult to manage <-> spark supports authentication via a shared secret

## Spark features
-> Resillent Distributed datasets (RDD)
-> Data is stored in the RAM

## Spark components
-> Spark Core -> base engine
    -> responsible for memoery management
    -> fault recovery
    -> scheduling, distributing and monitoring jobs on a cluster
    -> interacting with storage systems
-> Spark SQL
-> Spark streaming -> allows to real-time stream data to somewher
-> Spark MLlib -> for machine learning algorithms
-> GraphX -> finding relationships between data <-> graph based data 

## Resillent distributed datasets (RDD)
-> an immutable fault-tolerant, distributed collection of objects that can be operated on in parallel
-> It performs two main actions
    -> Transformations (map, filter, join, union) that are performed on rDD that yields a new RDD containing the result
    -> Action (reduce, first, count) that return a value after running a computation on an RDD

## Spark SQL
-> framework component is used for structured and semi-structured data processing
-> DSL, HQL or SQL may be executed over created dataframes (rows with columns <- meaning)

## Spark Streaming
-> Spark streaming is a lightweight API that allows developers to perform batch processing and real-time streaming of data with ease
-> allows batch and realtime streaming of data 

## Spark MLib
-> is a low-level machine learning library that is simple to use, is scalabale, and compatible with various programming languages

## GraphX
-> own graph computation engine and data store

## Spark architecture
-> Spark uses a master-slave architecture that consists of a driver, that runs on a master node, and multiple executors which run across the worker nodes in the cluster
-> spark applications run as indepentent sets of processes on a cluster
-> Master node includes driver program and driver program creaters spark context, which then connect to cluster manager (eg. YARN -> RM)
-> Resource manager (RM) makes request to NodeManager (MN) asking for conteiners, if request is approved, resource manager will execute 
application master will run of one of the conteiners, and then will be used another conteiners, which are included

## Spark Cluster managers
-> Standalone -> without hadoop -> each application will try to use all available nodes
-> Mesos
-> hadoop -> YARN is the cluster resource manager of Hadoop 2. Spark can be run on YARN
-> Kubernetes

# Spark architecture
## Resillient Distributed Dataset
-> RDD´s are the fundamental units of data in Apace Spark that are split into partitions and can be executed on different nodes of a cluster
## Directed Acyclic Graph (DAG)
-> DAG is the scheduling layer of the spark architecture that implements stage-oriented scheduling and eliminates the Hadoop MapReduce multistage execution model
## Master Node
-> Every master node has a driver program, every driver program has the entry point to application -> that is sparkContext
-> Spark context which takes application request to cluster manager

-> The driver program and Spark context takes care of the job execution within the cluster
## Cluster manager
-> as a source manager and negotiator to node managers
-> node managers will approve or reject resource request from source manager
-> if approved, containers will be given (containers are combination of CPU and RAM)

->a job split into multiple tasks that re distributed over the worker node
-> when an RDD is created in SPARK ocntext, it can be distributed across various nodes
-> worker nodes are slaves that execute different tasks
-> executor is responsible for the execution of these tasks
-> worker nodes execute the tasks assigned by the cluster manager and returns the resultback to the spark context
-> Worker nodes execute the tasks assigned by the cluster manager and returns it back to the spark context
-> executor is responsible for the execution of these tasks

## Spark Context
SparkContext represents the connection to a Spark cluster, and can be used to create RDD and broadcast variables on that cluster.


## commands
```
spark = (
    SparkSession
    .builder
    .appName("toy_application")
    .getOrCreate()
)
```
-> .appName('_name_') -> app name
-> .getOrCreate() -> assures, that session will be singleton, that means, if session does not exist, then session will be created or if already was created, getOrCreate will return this already created session

V tomto minimálním příkladu jsme sešnu pojmenovali (skrze *appName*) a poté jsme zavolali metodu *getOrCreate*. Ta zajistí, že šesna bude singleton. Tj. pokud sešna neexistuje, bude vytvořena, ale pokud už nějaká sešna předtím vznikla, *getOrCreate* vrátí právě tu. Toto chování si demonstrujme na zobrazení spark objektu a na vypsání jeho IDčka.  
Když vložíme do buňky samostojící jméno sešny, dostaneme odkaz na Spark UI - de facto webový inteface, ve kterém můžeme běh sešny kontrolovat. Pod labelem "Version" se skrývá verze Sparku, "Master" nám zase řekne, kde vlastně Spark bydlí. Důležité pro nás v tomto bodě je "AppName", kde vidíme jméno naší aplikace - toy_application.