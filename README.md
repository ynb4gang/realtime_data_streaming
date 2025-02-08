# Real-Time Data Streaming Pipeline

This project showcases a real-time data streaming pipeline using a combination of powerful tools and technologies, including **Apache Airflow**, **Apache Kafka**, **Apache Zookeeper**, **Apache Spark**, and **Cassandra**. The entire setup is containerized using **Docker**, making it easy to deploy and scale.

## Overview

The pipeline consists of the following components:

1. **Data Ingestion**: 
   - Data is ingested from the [randomuser.me](https://randomuser.me/) API using Apache Kafka.
   - The data is then formatted and streamed to a Kafka topic (`users_created`).

2. **Data Processing**:
   - Apache Spark processes the incoming data in real-time.
   - The processed data is then written to a Cassandra database.

3. **Data Storage**:
   - The processed data is stored in a Cassandra database for further analysis and querying.

4. **Orchestration**:
   - Apache Airflow is used to orchestrate the entire pipeline, ensuring that each component runs in the correct order and at the right time.

## Technologies Used

- **Apache Airflow**: For workflow orchestration and scheduling.
- **Apache Kafka**: For real-time data ingestion and streaming.
- **Apache Zookeeper**: For managing Kafka brokers.
- **Apache Spark**: For real-time data processing.
- **Cassandra**: For storing the processed data.
- **Docker**: For containerizing the entire setup.

## Project Structure

- **`docker-compose.yml`**: Defines the services for the entire pipeline, including Kafka, Zookeeper, Spark, Cassandra, and Airflow.
- **`spark_stream.py`**: Contains the Spark streaming logic to process data from Kafka and store it in Cassandra.
- **`kafka_stream.py`**: Contains the Kafka producer logic to ingest data from the API and stream it to Kafka.
- **`entrypoint.sh`**: A shell script to initialize the Airflow environment and install dependencies.
- **`requirements.txt`**: Lists all Python dependencies required for the project.
- **`.gitignore`**: Specifies files and directories to be ignored by Git.

## Getting Started

### Prerequisites

- Docker and Docker Compose installed on your machine.

### Steps to Run the Project

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/ynb4gang/realtime_data_streaming.git
   cd realtime_data_streaming
    ```
   
2. **Build and Start the Docker Containers:**
      ```bash
    docker-compose up -d
    ```
      
3. **Access the Airflow Web Interface:**
  Open your browser and go to **`http://localhost:8080`**.
  Use the default credentials (**`admin/admin`**) to log in.

4. **Trigger the DAG:**
  In the Airflow UI, find the **`user_automation`** DAG and trigger it to start the data ingestion and processing pipeline.

5. **Monitor the Pipeline:**
  - You can monitor the progress of the pipeline in the Airflow UI.
  - The processed data will be stored in the Cassandra database.

## Stopping the Project
To stop the containers, run:
 ```bash
 docker-compose down
 ```

## Conclusion
This project provides a comprehensive example of how to build a real-time data streaming pipeline using modern data engineering tools. It is a great starting point for anyone looking to understand the integration of Kafka, Spark, Cassandra, and Airflow in a real-world scenario.

Feel free to explore, modify, and extend the project to suit your needs!
