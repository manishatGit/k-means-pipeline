# k-means-pipline
### Using k-means pipline library to predict on categorical values

###Requirements
Spark version 1.5.0 or Higher  

##Running with Spark Shell:  
```{r, engine='bash', count_lines}
$ $SPARK_HOME/bin/spark-shell --packages knoldus:k-means-pipeline:0.0.1
```
###Or  
To include it with your Spark application, get the jar from [here](http://dl.bintray.com/spark-packages/maven/knoldus/k-means-pipeline/0.0.1/k-means-pipeline-0.0.1.jar)   
```scala
  import com.knoldus.pipeline.KMeansPipeLine

  val kMeans = new KMeansPipeLine()
   val df = sqlContext.createDataFrame(Seq(
    ("a@email.com", 12000,"M"),
    ("b@email.com", 43000,"M"),
    ("c@email.com", 5000,"F"),
    ("d@email.com", 60000,"M")
  )).toDF("email", "income","gender")
  
  val categoricalFeatures = List("gender","email")
  val numberOfClusters = 2
  val iterations = 10
  val predictionResult = kMeans.predict(sqlContext,df,categoricalFeatures,numberOfClusters,iterations)

```
