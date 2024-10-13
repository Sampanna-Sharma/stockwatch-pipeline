
# **StockWatch: Real-Time Analytics Pipeline**

StockWatch is an automated data engineering pipeline designed to extract, store, and analyze stock data in real-time. This project leverages Airflow for orchestration, Snowflake for data warehousing, and Quarto with Plotly for visualizing stock analytics. Data quality checks are performed with cuallee, and Minio provides S3-compatible object storage.

## **Features**

- **Automated Data Extraction**: Uses Airflow to schedule daily extraction of stock data from the Alpaca API.
- **Data Storage**: Efficiently stores and queries stock data using Snowflake as the data warehouse.
- **Real-Time Analytics**: Generates interactive stock analysis dashboards using Quarto and Plotly.
- **Data Quality Assurance**: Runs data validation checks with cuallee to ensure accuracy and consistency.
- **S3-Compatible Storage**: Manages data backups and long-term storage with Minio.

## **Architecture Overview**

1. **Data Extraction**: 
   - Airflow DAGs orchestrate daily tasks to pull stock data from Alpaca API.
2. **Data Storage**:
   - Postgres stores Airflow metadata and tracks upstream schemas.
   - Snowflake serves as the data warehouse for stock data, enabling high-performance queries.
3. **Analytics**:
   - Quarto and Plotly generate HTML reports and interactive dashboards, enabling real-time analysis of stock trends.
4. **Data Quality**:
   - cuallee ensures data integrity through automated validation checks.
5. **Data Storage**:
   - Minio provides S3-compatible storage for raw data, backups, and processed results.

## **Technologies Used**

- **Airflow**: Orchestrates DAGs to automate data extraction and processing.
- **Postgres**: Manages metadata and schema for data tracking.
- **Snowflake**: Acts as the data warehouse for storing and querying stock data.
- **Alpaca API**: Provides real-time stock market data.
- **Quarto + Plotly**: Powers the creation of interactive dashboards and HTML reports.
- **cuallee**: Runs data quality checks to ensure data accuracy.
- **Minio**: Offers S3-compatible object storage for data retention and backup.

## **Setup Instructions**

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/stockwatch-pipeline.git
   cd stockwatch-pipeline
   ```

2. **Install Dependencies**:
   - Set up a virtual environment and install dependencies:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

3. **Configure Airflow**:
   - Set up Airflow by initializing the database:
   ```bash
   airflow db init
   airflow users create --username admin --password admin --firstname Admin --lastname User --role Admin --email admin@example.com
   ```

4. **Set Up Snowflake and Minio**:
   - Ensure you have Snowflake credentials and Minio set up as your S3-compatible storage.

5. **Schedule the DAG**:
   - Start the Airflow scheduler and web server:
   ```bash
   airflow scheduler &
   airflow webserver &
   ```

6. **Run the Pipeline**:
   - The pipeline will automatically extract stock data daily, perform quality checks, and update dashboards. You can monitor progress in the Airflow UI.

## **Data Quality Checks**

The project leverages cuallee to ensure that all incoming data from the Alpaca API is accurate. Checks include:
- Ensuring no missing values in critical fields.
- Verifying valid stock prices and volume figures.
- Checking for anomalies in stock price trends.

## **Dashboard Preview**

You can view the real-time stock analysis dashboards in your browser, which are generated from Quarto and Plotly. The dashboards include:
- Stock price trends over time.
- Daily volume fluctuations.
- Key indicators and patterns in stock market data.
