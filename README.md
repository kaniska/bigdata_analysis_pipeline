# Bigdata analysis pipeline
| the idea is to create a map-reduce task for every step and connect the steps to create a pipeline.

## Fetch data
### HDFS
## Organize data
### Filter
#### Pig / Hive Script
##### Group By
##### Join
### Count
### Extract Entities (NLP Tesxt processing)
#### Find locations, time, place, organization
#### Apply Ontology ( Medical , Finance )
## Analyze data
### Social Networking ANalysis (SNA)
### Crawler 
#### Webscraper 
#### Twitter 
#### Facebook
#### LinkedIn
#### Stock Market
### Machine Learning (Classification, Clustering)
#### Vectorize data
##### convert input data folder into set of sequence files
##### convert sequenced data into sparse vectors for data analysis
#### Split data for Cross-validation
##### create training and test data files
#### Classification of data
##### Naive Bayes
####### [min doc freqn , max df % , max df sigma, , min log likelihood, log normalize , max NGram]
##### Decision Tree
###### 
#### Clustering of data
##### K-Means
##### Dirichlet
##### Min-Hash
## 
# Configuration
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
| delimiter , clusterDumper, outlierthreshold, convergenceDelta , distanceMeasure, 
| maxNgramSize , logNormalize, minLLR , maxDFPercent, minDF, maxDFSigma , numReducers
### Web Crawler Config :
| threads , followredirects , exclude extensions , include filters , exclude filters , maxdepth , max iterations
### Pig Analysis config
| specify the schema , join columns 
