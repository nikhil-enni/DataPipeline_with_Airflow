# DataPipeline_with_Airflow
Developed an ETL pipeline using Python and Airflow to ingest Sparkify's music data into AWS Redshift

**ETL Pipeline for Sparkify Music Data on AWS Redshift**:
This repository provides an Extract, Transform, Load (ETL) pipeline for ingesting Sparkify's music data into an AWS Redshift Data Warehouse. The ETL pipeline is designed to run on an hourly basis and is scheduled using Airflow.

**Why Airflow?**:
Airflow is chosen as the workflow management tool because it allows workflows to be defined as code, making them more maintainable, versionable, testable, and collaborative. Airflow provides a user-friendly interface to manage and monitor workflows, making it an ideal choice for scheduling and orchestrating the ETL pipeline.

**Purpose**:
The purpose of this database is to enable Sparkify to answer various business questions about its users, the types of songs they listen to, and the artists of those songs using the data available in logs and files. The database provides a consistent and reliable source to store and analyze this data.

The data stored in the database can be utilized to achieve several analytical goals, such as identifying songs with the highest popularity or determining peak traffic times during the day.

**Dependencies**:
Before running the ETL pipeline, ensure that the following dependencies are met:

1. Airflow: Install Airflow by running pip install airflow.
2. PostgreSQL: Configure PostgreSQL to store metadata from Airflow jobs. Edit the airflow.cfg file under the AIRFLOW_HOME directory. Refer to this gist for setup instructions.
3. AWS Redshift: Configure Redshift connection in Airflow to enable data ingestion. This can be done through the Airflow UI by navigating to Admin > Connections.
4. AWS Credentials: Configure AWS credentials in Airflow using access and secret access keys. This can also be done through the Airflow UI by navigating to Admin > Connections.

**Design and ETL Pipeline**:
The ETL pipeline follows a STAR schema design, which simplifies queries and provides fast aggregations of data. The pipeline is implemented in Python, leveraging libraries such as Pandas for data manipulation and reading files from Amazon S3.

The pipeline processes two types of data: song data and log data.

1. Song Data: Contains information about songs and artists. This data is extracted and loaded into the users and artists dimension tables.
2. Log Data: Provides information about each user session. From the log data, the pipeline extracts and loads data into the time, users, and songplays fact tables.

**Running the ETL Pipeline**:
To run the ETL pipeline, follow these steps:

1. Start the Airflow web server by running airflow webserver -p 8080.
2. Turn on the sparkify_music_dwh_dag DAG in the Airflow UI. This will automatically trigger the ETL pipeline to run.
You can monitor the progress and status of the pipeline through the Airflow UI, which provides visual representations of the workflows.



