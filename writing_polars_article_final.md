# **Introduction to Pandas**
 One of the fastest Dataframe library at the moment.  
![Polars](https://github.com/bmwathie/Examen_Python-M1_IA_Nov_2022/blob/main/img/t%C3%A9l%C3%A9chargement.png?raw=true "Polars")
# **Contents**
- **Introduction**
- **Concept**
- **Installing Polars**
- **Creating a Polars DataFrame**
- **Importants attributes and function to know**
- **Potential alternatives**
- **Data processing with Polars**
## **Introduction**
**Polars** library is a ast in-memory tabular data processing library designed to be used in conjunction with Python. It was developed to offer high performance and advanced features for processing large-scale data. In this presentation, we will review the fundamental concepts of Polars, as well as practical examples, potential alternatives, and use cases.
## **Concept**
Polars is a Python library for in-memory tabular data processing that provides advanced features for handling large-scale data. It is designed to be a performant and efficient alternative to traditional data processing libraries like Pandas. Polars leverages Rust, a high-performance systems programming language, to provide the necessary speed and performance for large datasets.

Polars uses a DataFrame as its core data structure, similar to Pandas. However, unlike Pandas, Polars is designed to handle larger datasets efficiently by taking advantage of Rust's memory management and parallelism features. Polars supports a wide range of data types and operations, including filtering, grouping, aggregating, and joining data.
## **Installing Polars**
To install Polars, you can simply use the `pip` command :  
`pip install polars`  
Or, use the `conda` command :  
`conda install polars`  
## **Creating a Polars DataFrame**
The best way to learn a new library is to get your hands dirty. Let's get started by importing the ***polars*** module and creating a Polars DataFrame:  
```python
import polars as pl
df = pl.DataFrame(
    {
        'Name': ['mbaye','moustapha','cheikh','patrick','aliou',
                    'charles','jean','jhon','anna','christine'],
        'email': ['mbaye@gmail.com','moustapha@gmail.com','cheikh@gmail.com', 'patrick@gmail.com','aliou@gmail.com',     
                  'charles@gmail.com','jean@gmail.com','jhon@gmail.com','anna@gmail.com','christine@gmail.com'],
        'salary en FCFA': [350000, 250000, 150000, 1300000, 175000, 500000, 900000, 850000, 175000, 235000]
    }
)
df  
```
![output](https://github.com/bmwathie/Examen_Python-M1_IA_Nov_2022/blob/main/img/Capture%20d%E2%80%99%C3%A9cran%20du%202023-03-06%2016-37-06.png?raw=true "output")  
Polars expects the column header names to be of string type. Consider the following example:  
```python
df2 = pl.DataFrame(
    {
        0 : [1,2,3],
        1 : [80,170,130],
    }
)
```
The above code snippet won't work as the keys in the dictionary are of type integer (0 and 1). To make it work, you need to make sure the keys are of string type (“0” and “1”):  
```python
df2 = pl.DataFrame(
    {
        "0" : [1,2,3],
        "1" : [80,170,130],
    }
)
```  
Besides displaying the header name for each column, Polars also displays the data type of each column. 
## **Important attributes and function to know**  
- **.dtypes** : display the data type
- **.columns** : to get the column names  
- **.rows()** : to get the content of the DataFrame as a list of tuples 
- **.row()** : displays a specific row (the specification is done between parentheses, ex: df.row(0)). The result is a tuple.
- **.select()** : displays data from the specified column  
- **.filter()** : to select multiple rows  
- **.groupby(), .agg(), .pivot_table()** : functions allow to aggregate data using various aggregation functions such as sum, average, maximum, minimum, etc.
- **.Join(), .merge()** : functions allow to join data from multiple dataframes.  

Note that this list is not exhaustive, for more details you can consult the complete documentation : https://pola-rs.github.io/polars/py-polars/html/reference/dataframe/index.html  
## **Potential alternatives**  
These are some tools that share similar functionality to what polars does.

- Pandas:  
    * A very versatile tool for small data. Read 10 things I hate about pandas written by the author himself. Polars has solved all those 10 things. Polars is a versatile tool for small and large data with a more predictable API, less ambiguous and stricter API.
- Pandas the API :  
    * The API of pandas was designed for in memory data. This makes it a poor fit for performant analysis on large data (read anything that does not fit into RAM). Any tool that tries to distribute that API will likely have a suboptimal query plan compared to plans that follow from a declarative API like SQL or polars' API.
- Dask :   
    * Parallelizes existing single-threaded libraries like NumPy and Pandas. As a consumer of those libraries Dask therefore has less control over low level performance and semantics. Those libraries are treated like a black box. On a single machine the parallelization effort can also be seriously stalled by pandas strings. Pandas strings, by default, are stored as python objects in numpy arrays meaning that any operation on them is GIL bound and therefore single threaded. This can be circumvented by multi-processing but has a non-trivial cost.
- Modin :  
    * Similar to Dask
- Vaex :

    * Vaexs method of out-of-core analysis is memory mapping files. This works until it doesn't. For instance parquet or csv files first need to be read and converted to a file format that can be memory mapped. Another downside is that the OS determines when pages will be swapped. Operations that need a full data shuffle, such as sorts cannot benefit from memory mapping. At the moment of writing vaex relies on pyarrow for sorts, meaning that the data must fit into memory.
    * Polars' out of core processing is not based on memory mapping, but on streaming data in batches (and spilling to disk if needed), we control which data must be hold in memory, not the OS, meaning that we don't have unexpected IO stalls.
- DuckDB :  
    * Polars and DuckDB have many similarities. DuckDB is focussed on providing an in-process OLAP Sqlite alternative, polars is focussed on providing a scalable DataFrame interface to many languages. Those different front-ends lead to different optimization strategies and different algorithm prioritization. The interop between both is zero-copy. See more: https://duckdb.org/docs/guides/python/polars
- Spark :  
    * Spark is designed for distributed workloads and uses the JVM. The setup for spark is complicated and the startup-time is slow. Polars has much better performance characteristics on a single machine. The API's are somewhat similar.
- CuDF  
    * GPU's are fast, but not readily available and expensive in production. The amount of memory available on GPU often is a fraction of available RAM. Next to that Polars is close in performance to CuDF and on some operations even faster. CuDF also doesn't optimize your query, so it is likely that on ETL jobs polars will be faster because it can elide unneeded work and materialization's.
- Any :  
    * Polars is written in Rust. This gives it strong safety, performance and concurrency guarantees. Polars is written in a modular manner. Parts of polars can be used in other query program and can be added as a library.
## **Data processing with Polars**
What's better than practice to learn?  
Polars already offers many functionalities that we are already familiar if you have worked with Pandas before. We can find an overview, including examples (for most), in the reference guide : https://pola-rs.github.io/polars/py-polars/html/reference/dataframe/index.html  
Link to the dataset used : https://www.kaggle.com/datasets/zynicide/wine-reviews?resource=download 







