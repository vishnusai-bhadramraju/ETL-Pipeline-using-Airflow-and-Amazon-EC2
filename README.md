# ETL Pipeline for Weather Data

This project implements an ETL (Extract, Transform, Load) pipeline for retrieving weather data from a weather API, transforming the data using Python, and loading the transformed data into an S3 bucket. Apache Airflow is used for scheduling and managing the ETL tasks.

## Table of Contents

- [Project Overview](#project-overview)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [License](#license)

## Project Overview

The ETL pipeline automates the process of collecting weather data, transforming it into a desired format, and storing it in an S3 bucket for further analysis and processing. The pipeline is scheduled and monitored using Apache Airflow, ensuring reliable and repeatable workflows.

## Architecture

1. **Extraction**: Retrieve weather data from a weather API.
2. **Transformation**: Process and transform the raw data using Python.
3. **Loading**: Upload the transformed data to an AWS S3 bucket.

## Technologies Used

- **Apache Airflow**: For scheduling and managing the ETL workflow.
- **Python**: For data transformation and processing.
- **AWS S3**: For storing the transformed data.
- **Weather API**: Source of the weather data.

## Installation

### Prerequisites

- Python 3.6+
- Apache Airflow
- AWS CLI configured with appropriate access to S3

### Steps

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/your-username/etl-weather-pipeline.git
    cd etl-weather-pipeline
    ```

2. **Set Up Python Environment**:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
    ```

3. **Install and Configure Airflow**:
    ```bash
    export AIRFLOW_HOME=~/airflow
    pip install apache-airflow
    airflow db init
    airflow users create \
        --username admin \
        --firstname Admin \
        --lastname User \
        --role Admin \
        --email admin@example.com
    ```

4. **Start Airflow**:
    ```bash
    airflow webserver --port 8080
    airflow scheduler
    ```

## Configuration

### Airflow Configuration

Ensure the following Airflow variables and connections are set up:

- **Variables**:
    - `weather_api_url`: URL of the weather API endpoint.
    - `s3_bucket_name`: Name of the S3 bucket where data will be loaded.

- **Connections**:
    - `aws_default`: AWS connection with access to S3.
    - `http_weather_api`: HTTP connection for the weather API.

### DAG Configuration

Edit the DAG configuration in `dags/etl_weather_dag.py` as needed.

## Usage

1. **Access Airflow UI**:
   Open your browser and go to `http://localhost:8080`. Log in with your Airflow credentials.

2. **Trigger the DAG**:
   In the Airflow UI, enable and trigger the `etl_weather_dag`.

3. **Monitor the Pipeline**:
   Monitor the execution of the tasks in the Airflow UI. Check logs for any errors and ensure data is loaded into the S3 bucket.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to contribute to this project by opening issues or submitting pull requests. For any questions, please contact [vishnusaibhadramraju1@gmail.com](mailto:yVoishnusaibhadramraju1@gmail.com).
