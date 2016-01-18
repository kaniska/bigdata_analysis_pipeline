# Bigdata analysis pipeline
* the idea is to create a map-reduce task for every step and connect the steps to create a pipeline.
* we can design a system where TaskMetaModel can contain necessary user params, system params and connector properties.
* such TaskMetaModels already tried and tested as Hadoop Jobs.
* now we can develop a SparkTaskMetaModels to generate Spark RDDs  to create in-memory distributed data analysis Pipeline
* possibly we can develop higher level abstractions for SciPy , NumPy , SciKit , R , Pig , Hive and simply expose them configurable and user-friendly WorkFLow MetaModels to build a Pipeline.

## Fetch data
##### HDFS
## Organize data
### Filter data
#### Pig / Hive Script
- Group By
- Join
- Count data
### Extract Entities (NLP Tesxt processing)
- Find locations, time, place, organization
- Apply Ontology ( Medical , Finance )
## Analyze data
### Social Networking ANalysis (SNA)
### Crawler 
- Webscraper 
- Twitter 
- Facebook
- LinkedIn
- Stock Market
### Machine Learning (Classification, Clustering)
- Vectorize data
- Convert input data folder into set of sequence files
- Convert sequenced data into sparse vectors for data analysis
- Split data for Cross-validation
- Create training and test data files
#### Classification of data
##### Naive Bayes
- [min doc freqn , max df % , max df sigma, , min log likelihood, log normalize , max NGram]
##### Decision Tree
###### 
#### Clustering of data
##### K-Means
##### Dirichlet
##### Min-Hash
## 
# Configuration
### CDH Hadoop Configuration :
Sample configuration for invoking a Decision Tree MR Job as a Workflow Step
#### User config
* useradd -U -G mapred,hdfs,hadoop -m -u 5000 demo
* usermod -G demo -a hdfs
* usermod -G demo -a mapred
* chmod 770 ~/demo
* Services->hdfs1->Configuration->View and Edit->Service Wide->Security , dfs.permissions.supergroup = hadoop
#### JVM settings
* mapreduce1 > configuration > TaskTracker > Performance > mapred.child.java.opts : -Djavax.xml.parsers.DocumentBuilderFactory =com.sun.org.apache.xerces.internal.jaxp.DocumentBuilderFactoryImpl
* hdfs1 > configuration > NameNode > Advanced > Java Configuration Options for NameNode : -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:- CMSConcurrentMTEnabled -XX:CMSInitiatingOccupancyFraction=70 - XX:+CMSParallelRemarkEnabled -Dcom.sun.management.jmxremote - Dcom.sun.management.jmxremote.authenticate=false -
Dcom.sun.management.jmxremote.ssl=false - Dcom.sun.management.jmxremote.port=25002
* hdfs1 > configuration > DataNode > Advanced > Java Configuration Options for DataNode : XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:- CMSConcurrentMTEnabled -XX:CMSInitiatingOccupancyFraction=70 - XX:+CMSParallelRemarkEnabled -Dcom.sun.management.jmxremote - Dcom.sun.management.jmxremote.authenticate=false - Dcom.sun.management.jmxremote.ssl=false - Dcom.sun.management.jmxremote.port=25001
* mapreduce1 > configuration > JobTracker > Advanced > Java Configuration Options for JobTracker : -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:- CMSConcurrentMTEnabled -XX:CMSInitiatingOccupancyFraction=70 -XX:+CMSParallelRemarkEnabled -Dcom.sun.management.jmxremote - Dcom.sun.management.jmxremote.authenticate=false -
Dcom.sun.management.jmxremote.ssl=false - Dcom.sun.management.jmxremote.port=25000
### Firewall config :
* open ports for SSH (22) , JMX (25001-25002) , Namendoe (9000) , Jobtracker (9001) , Server (8080)
### Sparse vector config :
#### Hadoop / Mahout specific setting
* minDF = minimum document frequency
* maxDF % = max % of documents for the so that 'very high frequency terms presented as integer btn 0 - 100 can be removed(default 10)
* maxDFsigma = amount of TF-IDF vectors (expressed in terms of Std. Dev.) as double (default 3.0)
* minLLR = minimum log likelihood ratio (float)
* maxNGram = 2 (biGram) , 3 (triGram)
* logNormalize = (true / false) , normalization value (INFINTE)
* sequentialAccess
### Naive Bayes config :
#### Hadoop / Mahout specific setting
* above DF , LLR , NGram settings are applicable here
* 
### Decision Tree config :
#### Mahout partial decision forest
* regression 
* selection (default -> sq root of #explanatory vars)
* minprop (tree node not divided any further if proportion of variance of branching < minprop)
* seed 
* nbtree ( how to grow the tree)
* minsplit (default = 2)
#### Breiman Decision Forest
* regression , #nbtrees , #iterations
### KMeans Config
* delimiter , clusterDumper, outlierthreshold, convergenceDelta , distanceMeasure, 
* maxNgramSize , logNormalize, minLLR , maxDFPercent, minDF, maxDFSigma , numReducers
### Web Crawler Config :
* threads , followredirects , exclude extensions , include filters , exclude filters , maxdepth , max iterations
### Pig Analysis config
* specify the schema , join columns 
