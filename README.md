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
    'user':'*****',
    'password':'*****'
   }

   conn = psycopg2.connect(**db_config)
   ```
5. [E]xtract -- read parquet & convert into pandas data frame
   ```python3
   df = pd.read_parquet('CO2 Emission Country.parquet')
   ```
7. [T]ransform -- remove uncessary string & conver to numeric
   ```python3
   df['% of global total'] = df['% of global total'].str.replace('%', '', regex=False)
   ```
   ```python3
   df['Fossil emissions 2023'] = pd.to_numeric(df['Fossil emissions 2023'], errors='raise')
   ```
9. [L]oad -- load pandas to postgres
   ```python3
   engine = create_engine(f"postgresql+psycopg2://{db_config['user']}:{db_config['password']}@{db_config['host']}:{db_config.get('port', 5432)}/{db_config['database']}")
   df.to_sql(table_name, engine, if_exists='append', index=False)
   ```
