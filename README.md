

# Real-Time Data Streaming Pipeline 🚀

A comprehensive end-to-end data engineering project that demonstrates real-time data processing at scale.

## 🌟 Overview

Transform and process data in real-time using a modern data engineering stack. This project showcases a production-ready pipeline that handles data ingestion, processing, and storage using industry-standard tools and best practices.

## 🏗️ Architecture

Our pipeline consists of several key components working together:

```mermaid
flowchart LR
    api[("API")]
    pg[(PostgreSQL)]
    af[Apache Airflow]
    zk[ZooKeeper]
    kf[Kafka]
    cc[Control Center]
    sr[Schema Registry]
    spark_master[Spark Master]
    w1[Spark Worker 1]
    w2[Spark Worker 2]
    w3[Spark Worker 3]
    w4[Spark Worker 4]
    cass[(Cassandra)]

    api --> af
    af --> pg
    af -- "Streaming" --> kf
    zk --> kf
    kf --> cc
    kf --> sr
    kf -- "Streaming" --> spark_master
    spark_master --> w1
    spark_master --> w2
    spark_master --> w3
    spark_master --> w4
    w1 -- "Streaming" --> cass
    w2 -- "Streaming" --> cass
    w3 -- "Streaming" --> cass
    w4 -- "Streaming" --> cass

    classDef database fill:#f5f5f5,stroke:#333,stroke-width:2px
    classDef service fill:#e1f5fe,stroke:#333,stroke-width:2px
    classDef monitoring fill:#e8f5e9,stroke:#333,stroke-width:2px
    classDef worker fill:#fff3e0,stroke:#333,stroke-width:2px

    class api,pg,cass database
    class af,zk,kf service
    class cc,sr monitoring
    class w1,w2,w3,w4,spark_master worker
```

### Component Breakdown
- **Data Ingestion**: Random user data from `randomuser.me` API
- **Workflow Management**: Apache Airflow with PostgreSQL backend
- **Stream Processing**: Apache Kafka + Zookeeper
- **Data Processing**: Apache Spark cluster
- **Storage**: Apache Cassandra
- **Monitoring**: Kafka Control Center + Schema Registry

## 🛠️ Tech Stack

| Category | Technologies |
|----------|-------------|
| Core Processing | Apache Airflow, Apache Spark |
| Streaming | Apache Kafka, Apache Zookeeper |
| Storage | PostgreSQL, Apache Cassandra |
| Containerization | Docker |
| Programming | Python |

## ✨ Features

- Real-time data streaming and processing
- Fault-tolerant architecture
- Scalable design
- Docker containerization
- Monitoring and schema management
- Automated workflow orchestration

## 📋 Prerequisites

- Python 3.11
- Docker and Docker Compose
- Minimum 16GB RAM recommended
- 50GB free disk space

## 🚀 Quick Start

1. **Set Up Environment**
   ```bash
   # Create and activate conda environment
   conda create -n data-pipeline python=3.11
   conda activate data-pipeline
   ```

2. **Install Dependencies**
   ```bash
   # Core dependencies
   pip install apache-airflow kafka-python cassandra-driver spark pyspark
   ```

3. **Configure Credentials**
   ```bash
   # Airflow credentials
   Username: admin
   Password: admin
   ```

4. **Launch Services**
   ```bash
   # Clone repository
   git clone https://github.com/Shaabanm2018/ETL-Data-Streaming-Project.git
   cd e2e-data-engineering

   # Start services
   docker-compose up -d
   ```

## 🔍 Service URLs

| Service | URL | Description |
|---------|-----|-------------|
| Airflow | http://localhost:8080 | DAG management |
| Control Center | http://localhost:9021 | Kafka monitoring |
| Spark Master | http://localhost:8081 | Spark management |

## 📸 System Screenshots & Results

### Apache Airflow Dashboard

![Screenshot 2024-10-31 193632](https://github.com/user-attachments/assets/1d26b43b-4d16-415c-959b-0e87deaae541)
*Apache Airflow Login Screen*

![Screenshot 2024-10-31 193209](https://github.com/user-attachments/assets/d8c9f9b7-0bee-487f-ab3c-6b8f4bf138e0)
*Apache Airflow DAGs showing our data pipeline workflows*

### Kafka Control Center

![Screenshot 2024-10-31 193849](https://github.com/user-attachments/assets/e92eda2c-6ee2-4820-b83f-3d045be5da13)
*Kafka Control Center showing active topics and throughput*

![Screenshot 2024-10-31 193257](https://github.com/user-attachments/assets/100832ff-e153-490f-8e9d-c51b4198c404)
*Real-time monitoring of data streams*

### Apache Cassandra Results
![Screenshot 2024-10-31 193459](https://github.com/user-attachments/assets/6b87dded-cab6-41da-bc6d-8de39a405087)


## 📦 Project Structure

```
ETL-Data-Streaming-Project/
├── airflow/
│   ├── dags/
│   └── logs/
├── kafka/
│   └── config/
├── spark/
│   └── apps/
├── cassandra/
│   └── data/
└── docker-compose.yml
```

⭐ Don't forget to star this repo if you found it helpful!
