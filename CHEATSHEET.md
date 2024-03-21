# Creating dataset:
According to documentation (https://cloud.google.com/bigquery/docs/datasets#bq)

```bash
bq --location=europe-central2 mk \
    --dataset \
    --description="DESCRIPTION" \
    hoetpng-acn-gcp-school:DATASET_ID
```
* Billing model set as default which is logical.
* No table or partition expiration.
## To check if dataset is created succesfully:

```bash
bq show \
  --project_id=hoetpng-acn-gcp-school \
  --dataset \
  hoetpng-acn-gcp-school:DATASET_ID
```
________________________________________________________________________________________________
# Creating Biglake External Tables for Raw Layer (for Raw all created tables will be 't_ext_bl'):

## Name conventions:
* 'fact_'
* 'dim_'

## Fact tables according to documentation:
https://www.tpc.org/tpc_documents_current_versions/pdf/tpc-ds_v3.2.0.pdf

## By using `BQ QUERY` with job id:

```bash
bq query --location=europe-central2 --project_id=hoetpng-acn-gcp-school --use_legacy_sql=false --job_id=SPECIFIED_JOB_ID 'SQL_STATEMENT_HERE'
```

### SQL DDL statement example:

```sql
CREATE OR REPLACE EXTERNAL TABLE `hoetpng-acn-gcp-school`.DATASET_ID.TABLE_ID (
  i_item_sk   STRING,
  i_item_id   STRING,
  i_rec_start_date   STRING,
  i_rec_end_date   STRING,
  i_item_desc   STRING,
  i_current_price   STRING,
  i_wholesale_cost   STRING,
  i_brand_id   STRING,
  i_brand   STRING,
  i_class_id   STRING,
  i_class   STRING,
  i_category_id   STRING,
  i_category   STRING,
  i_manufact_id   STRING,
  i_manufact   STRING,
  i_size   STRING,
  i_formulation   STRING,
  i_color   STRING,
  i_units   STRING,
  i_container   STRING,
  i_manager_id   STRING,
  i_product_name   STRING,
)
WITH CONNECTION `hoetpng-acn-gcp-school`.`europe-central2`.`biglake-gcs-connector` -- CONNECTOR_ID
OPTIONS (
  description="DESCRIPTION",
  skip_leading_rows=0,
  format='CSV',
  uris=["URI_SOURCE"],
  field_delimiter="|",
  max_staleness=INTERVAL 48 HOUR,
  metadata_cache_mode="AUTOMATIC",
  hive_partition_uri_prefix = '=gs://acn-gcp-school-tpc-ds-100-csv-t-ext-bl/item/{dt:DATE}/{val:STRING}',
  require_hive_partition_filter = false);
```

#### max_staleness:
In docs: https://cloud.google.com/bigquery/docs/reference/standard-sql/lexical#interval_literals

```sql
-- 0 years, 0 months, 0 days, 10 hours, 20 minutes, 30 seconds (0-0 0 10:20:30.520)
INTERVAL '10:20:30.52' HOUR TO SECOND

-- 1 year, 2 months, 0 days, 0 hours, 0 minutes, 0 seconds (1-2 0 0:0:0)
INTERVAL '1-2' YEAR TO MONTH

-- 0 years, 1 month, -15 days, 0 hours, 0 minutes, 0 seconds (0-1 -15 0:0:0)
INTERVAL '1 -15' MONTH TO DAY

-- 0 years, 0 months, 1 day, 5 hours, 30 minutes, 0 seconds (0-0 1 5:30:0)
INTERVAL '1 5:30' DAY TO MINUTE
```

#### JSON:
```sql
CREATE OR REPLACE EXTERNAL TABLE `project-id.dataset.table_name`
OPTIONS (
  format = 'NEWLINE_DELIMITED_JSON',
  uris = ['gs://bucket/folder/*.json'],
  ignore_unknown_values = true
);

```

#### AVRO:
```sql
CREATE OR REPLACE EXTERNAL TABLE `project-id.dataset.table_name`
OPTIONS (
  format = 'AVRO',
  uris = ['gs://bucket/folder/*.avro']
);

```

#### PARQUET:
```sql
CREATE OR REPLACE EXTERNAL TABLE `project-id.dataset.table_name`
OPTIONS (
  format = 'PARQUET',
  uris = ['gs://bucket/folder/*.parquet']
);


```
_________________________________________________________________________________

# Creating Views for Enriched Layer (for Enriched created tables will be VIEW '_v' or MATERIALIZED VIEW'_mv'):

## Name conventions:
* 'fact_'
* 'dim_'

## Fact tables according to documentation:
https://www.tpc.org/tpc_documents_current_versions/pdf/tpc-ds_v3.2.0.pdf


## By using `BQ QUERY` with job id:

```bash
bq query --location=europe-central2 --project_id=hoetpng-acn-gcp-school --use_legacy_sql=false --job_id=SPECIFIED_JOB_ID 'SQL_STATEMENT_HERE'
```

### SQL DDL statement example:

```sql
CREATE MATERIALIZED VIEW `hoetpng-acn-gcp-school`.acn_gcp_school_amxsk_02_enriched.dim_customer_mv OPTIONS (
  description="View with correct data types and derived columns - Each row in this dimension table represents a customer.",
  labels = [
    STRUCT("source", "tpc-ds")
  ],
max_staleness = INTERVAL 2 DAY
) AS SELECT 

CAST(c_customer_sk AS INTEGER) AS c_customer_sk,
CAST(c_customer_id AS STRING) AS c_customer_id,
CAST(c_current_cdemo_sk AS INTEGER) AS c_current_cdemo_sk,
CAST(c_current_hdemo_sk AS INTEGER) AS c_current_hdemo_sk,
CAST(c_current_addr_sk AS INTEGER) AS c_current_addr_sk,
CAST(c_first_shipto_date_sk AS INTEGER) AS c_first_shipto_date_sk,
CAST(c_first_sales_date_sk AS INTEGER) AS c_first_sales_date_sk,
CAST(c_salutation AS STRING) AS c_salutation,
CAST(c_first_name AS STRING) AS c_first_name,
CAST(c_last_name AS STRING) AS c_last_name,
CAST(c_preferred_cust_flag AS STRING) AS c_preferred_cust_flag,
CAST(c_birth_day AS INTEGER) AS c_birth_day,
CAST(c_birth_month AS INTEGER) AS c_birth_month,
CAST(c_birth_year AS INTEGER) AS c_birth_year,
CAST(c_birth_country AS STRING) AS c_birth_country,
CAST(c_login AS STRING) AS c_login,
CAST(c_email_address AS STRING) AS c_email_address,
CAST(c_last_review_date_sk AS INTEGER) AS c_last_review_date_sk,
CONCAT(
    COALESCE(c_salutation, ""),
    " ",
    COALESCE(c_first_name, "<Unknown>"),
    " ",
    COALESCE(c_last_name, "<Unknown>")
  ) AS c_derived_full_name,
INITCAP(c_birth_country) AS c_standarized_birth_country,
FORMAT_DATE("%Y-%m-%d", DATE(CONCAT(c_birth_year, "-", c_birth_month, "-", c_birth_day))) AS c_standarized_birth_date 
FROM `hoetpng-acn-gcp-school.acn_gcp_school_amxsk_01_raw.dim_customer_t_ext_bl`
```

## EXAMPLES FOR STANDARIZED, DEVIRED, CALCULATED:

Standardized Columns:

For standardized columns such as Date, Time, Currency, and Location, you can use functions like PARSE_DATE, PARSE_TIMESTAMP, FORMAT_DATE, FORMAT_TIMESTAMP, FORMAT_NUMBER, and FORMAT_TIME.
Derived Columns:

Use SQL expressions and functions to derive new columns from existing ones. Examples include:
Arithmetic operations: Addition (+), Subtraction (-), Multiplication (*), Division (/)
String manipulation: CONCAT, SUBSTR, LOWER, UPPER, REGEXP_EXTRACT, etc.
Date and time functions: DATE_DIFF, DATE_ADD, DATE_SUB, EXTRACT, etc.
Conditional expressions: CASE, IF, COALESCE, etc.
Mathematical functions: ABS, ROUND, CEIL, FLOOR, etc.
Computed Columns:

Computed columns are typically calculated on the fly when data is accessed, rather than being stored physically. You can use similar functions as for derived columns, but these expressions are often used within queries rather than being stored as part of the table definition.
Window functions: Functions like SUM, AVG, MAX, MIN, ROW_NUMBER, LAG, LEAD, etc., allow you to perform calculations over partitions or ranges of rows within a dataset.
Aggregate functions: Functions like COUNT, SUM, AVG, MIN, MAX, etc., can be used to compute aggregate values across rows in a dataset.
Scalar functions: Scalar functions perform computations on a single input value and return a single output value. Examples include mathematical functions (ABS, ROUND, SQRT, etc.) and string functions (LENGTH, TRIM, LEFT, RIGHT, etc.).

* DATE DIFFERENCE:
```sql
DATE_DIFF(CURRENT_DATE(), birth_date, YEAR)
```
YEAR: Difference in full years.
QUARTER: Difference in quarters.
MONTH: Difference in months.
DAY: Difference in days.
HOUR: Difference in hours.
MINUTE: Difference in minutes.
SECOND: Difference in seconds.

* EXTRACTION:
```sql
EXTRACT(YEAR FROM TIMESTAMP(DATE(ss.sold_date)))
```
YEAR: Extracts the year from a TIMESTAMP or DATE.
QUARTER: Extracts the quarter (1-4) from a TIMESTAMP or DATE.
MONTH: Extracts the month (1-12) from a TIMESTAMP or DATE.
DAY: Extracts the day of the month (1-31) from a TIMESTAMP or DATE.
DAYOFWEEK: Extracts the day of the week (1-7, where Sunday is 1) from a TIMESTAMP or DATE.
DAYOFYEAR: Extracts the day of the year (1-366) from a TIMESTAMP or DATE.
WEEK: Extracts the ISO 8601 week number (1-53) from a TIMESTAMP or DATE.
HOUR: Extracts the hour (0-23) from a TIMESTAMP.
MINUTE: Extracts the minute (0-59) from a TIMESTAMP.
SECOND: Extracts the second (0-59) from a TIMESTAMP.
MILLISECOND: Extracts the millisecond (0-999) from a TIMESTAMP.
MICROSECOND: Extracts the microsecond (0-999999) from a TIMESTAMP.
NANOSECOND: Extracts the nanosecond (0-999999999) from a TIMESTAMP.
TIME: Extracts the time portion of a TIMESTAMP.
DATE: Extracts the date portion of a TIMESTAMP.
TIMEZONE_HOUR: Extracts the time zone offset in hours from a TIMESTAMP.
TIMEZONE_MINUTE: Extracts the time zone offset in minutes from a TIMESTAMP.
DATETIME: Extracts both the date and time from a TIMESTAMP.
TIMESTAMP_ADD: Adds a specified duration to a TIMESTAMP.
TIMESTAMP_SUB: Subtracts a specified duration from a TIMESTAMP.

* PARSING DATE/TIMESTAMP:
```sql
PARSE_DATE('%Y-%m-%d', '2024-03-25') 
-----
FORMAT_DATE("%Y-%m-%d", DATE(CONCAT(c_birth_year, "-", c_birth_month, "-", c_birth_day)))
-----
PARSE_TIMESTAMP('%Y-%m-%d %H:%M:%S', '2024-03-25 13:45:30')
-----
FORMAT_TIMESTAMP('%Y-%m-%d %H:%M:%S', TIMESTAMP '2024-03-25 13:45:30')
```

* FORMAT_NUMBER:
```sql
FORMAT_NUMBER(1234567.89, '#,###.00')
```

* FORMAT_TIME:
```sql
FORMAT_TIME('%H:%M:%S', TIME '13:45:30')
```

* FORMAT STRING:
```sql
FORMAT('%s, %s, %s, %s', street_number, street_name, city, state)
```

* COALESCE/CONCAT:
```sql
CONCAT(
    COALESCE(c_salutation, ""),
    " ",
    COALESCE(c_first_name, "<Unknown>"),
    " ",
    COALESCE(c_last_name, "<Unknown>")
  ) AS c_derived_full_name,
```

* GET LETTERS FROM STRING SUBSTR:
```sql
SUBSTR(c_birth_country, 1, 1) -- START FROM 1 GIVE 1 
```

* CUMULATIVE SUM:
```sql
SELECT
  date_column,
  SUM(sales_amount) OVER (ORDER BY date_column) AS cumulative_sales_total
FROM
  your_table;
```

* 7-DAY MOVING AVERAGE:
```sql
SELECT
  date_column,
  AVG(sales_amount) OVER (ORDER BY date_column ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS moving_avg_sales
FROM
  your_table;

```

* PERCENTAGE CHANGE COMPARED TO PREVIOUS PERIOD:
```sql
SELECT
  date_column,
  (sales_amount - LAG(sales_amount) OVER (ORDER BY date_column)) / LAG(sales_amount) OVER (ORDER BY date_column) AS sales_percent_change
FROM
  your_table;
```

* IF NULL:
```sql
IFNULL(birth_country, 'n/a')
```


