# parquet_to_postgres
# *Overview*
Project repo to demonstrate ETL process using parquet as input, data transformation using python pandas library, then load into postgresql as database. This repo to demonstrate data pipeline at simplest way to giving picture of ETL process.
# *Prerequisites*
To follow along this learning need to available below requirement on system:
- pyhhon3 with pandas library
  ```bash
  sudo apt install python3
  ```
  ```bash
  pip install pandas
  ```
- jupyter notebook installed
  ```bash
  pip install jupyter
  ```
- postgresql running on system
  ```bash
  sudo systemctl status postgresql
  ```
# *Project Flow*
Data ingestion from parquet to postgreSQL:
1. Import python library for data manipulation
   ```python3
   import pandas as pd
   ```
3. postgres connection
   ```python3
   from sqlalchemy import create_engine
   import psycopg2

   db_config = {
    'host':'localhost',
    'database':'parquetpostgres',
    'user':'postgres',
    'password':'postgres'
   }

   conn = psycopg2.connect(**db_config)
   ```
5. [E]xtract -- read parquet & convert into pandas data frame
6. [T]ransform -- remove uncessary string & conver to numeric
7. [L]oad -- load pandas to postgres
