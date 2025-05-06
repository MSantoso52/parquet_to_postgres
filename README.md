# parquet_to_postgres
Data ingestion from parquet to postgreSQL:
1. Import python library for data manipulation & postgres connection -- pandas, sqlalchemy & psycopg2
2. (E)xtract -- read parquet & conver into pandas data frame
3. (T)ransform -- remove uncessary string & conver to numeric
4. (L)oad -- load pandas to postgres
