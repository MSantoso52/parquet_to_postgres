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
1. Import python library for data manipulation & postgres connection -- pandas, sqlalchemy & psycopg2
2. [E]xtract -- read parquet & conver into pandas data frame
3. [T]ransform -- remove uncessary string & conver to numeric
4. [L]oad -- load pandas to postgres
