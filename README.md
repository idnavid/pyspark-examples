# Apache PySpark by Example
This is the repository for the LinkedIn Learning course Apache PySpark by Example. The full course is available from [LinkedIn Learning][lil-course-url].

## Creating a spark session
Initiate the process of building a SparkSession using the `builder` method.

Set the spark master using the `master` method. 
- Use "local" to indicates you want to run Spark locally.
- Use "[*]" indicates you want to use all available cores on your local machine.

Create the session 
- if a SparkSession already exists with the specified configuration, it will be returned.
- If no matching SparkSession exists, a new one will be created using the provided configuration. This approach helps avoid creating redundant sessions.

```
spark = SparkSession.builder.master("local[*]").getOrCreate()
```

### Instructor

Jonathan Fernandes [lil-course-url]: https://www.linkedin.com/learning/apache-pyspark-by-example?dApp=59033956&leis=LAA
