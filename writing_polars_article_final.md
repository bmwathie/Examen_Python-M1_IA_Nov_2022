# **Introduction to Pandas**
 One of the fastest Dataframe library at the moment.  
![Polars](https://github.com/bmwathie/Examen_Python-M1_IA_Nov_2022/blob/main/img/t%C3%A9l%C3%A9chargement.png?raw=true "Polars")
# **Contents**
- **Introduction**
- **Concept**
- **Installing Polars**
- **Creating a Polars DataFrame**
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
![output](https://github.com/bmwathie/Examen_Python-M1_IA_Nov_2022/blob/main/img/Capture%20d%E2%80%99%C3%A9cran%20du%202023-03-06%2016-37-06.png?raw=true)





