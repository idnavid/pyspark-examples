# Apache PySpark by Example
This is the repository for the LinkedIn Learning course Apache PySpark by Example. The full course is available from [LinkedIn Learning][lil-course-url].

## Creating a spark session (locally)
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

## Read dataframe 
To read a csv file, use the `read.csv` method. 

Create a `Date` column from by converting the existing `Date` column into timestamp using the `to_timestamp` method. 
- `.withColumn('Date', ...)` means to either modify an existing column named 'Date' or create a new one with that name.
- `to_timestamp(col('Date'),'MM/dd/yyyy hh:mm:ss a')` converts the data within the existing 'Date' column into a timestamp data type with the formatting pattern 'MM/dd/yyyy hh:mm:ss a'.
- `col('Date')` selects the existing 'Date' column.

Filter to dates before a certain date using the `filter` method. 
- `lit('2018-11-11')` creates a literal timestamp representing November 11th, 2018.


```
from pyspark.sql.functions import to_timestamp, col, lit
rc = spark.read.csv('reported-crimes.csv', header=True
                    ).withColumn('Date', to_timestamp(col('Date'),'MM/dd/yyyy hh:mm:ss a')
                                 ).filter(col('Date') <= lit('2018-11-11'))
```

## Quick stats

The `show` method displays rows. 
```
rc.show(5)  # display the top 5 rows. 
```

The `count` method counts the number of rows (aka entries). 
```
rc.count()
```


### Instructor

Jonathan Fernandes [lil-course-url]: https://www.linkedin.com/learning/apache-pyspark-by-example?dApp=59033956&leis=LAA
