# Docker Compose Setup for OpenSearch, Prometheus, Grafana, Seq, and ClickHouse

This repository contains Docker Compose configurations for setting up and managing various services commonly used in logging, monitoring, and data management. Each service is containerized and ready to use with default configurations.

## Services Included

1. **OpenSearch**: A distributed search and analytics engine.
2. **Prometheus**: A powerful time-series database used for monitoring and alerting.
3. **Grafana**: A data visualization and monitoring tool that integrates with multiple data sources (such as Prometheus).
4. **Seq**: A structured log server for event streaming and log management.
5. **ClickHouse**: A fast open-source columnar database for real-time analytics.

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-repo-name.git
cd your-repo-name
```

### 2. Running the Services

To start all services in detached mode, run:

```bash
docker-compose up -d
```

This will pull the necessary Docker images and set up the containers for all the services defined in the `docker-compose.yml` files.

### 3. Access the Services

* **Grafana**: Access the Grafana dashboard at http://localhost:3000 with the default login:
   * Username: `admin`
   * Password: `admin` (can be changed in the `docker-compose.yml`)
* **Prometheus**: Access Prometheus at http://localhost:9090
* **Seq**: Access Seq at http://localhost:5341
* **ClickHouse**: Access ClickHouse at http://localhost:8123
* **OpenSearch**: Access OpenSearch at http://localhost:9200

### 4. Stopping the Services

To stop the services, run:

```bash
docker-compose down
```

This will stop and remove the containers, but the data volumes will be retained.

## Services Configuration

### OpenSearch
* Configured with 2 nodes, memory settings adjusted for ML workloads
* Security plugin enabled, and initial admin password is set

### Prometheus
* Configured to scrape metrics from other services (e.g., OpenSearch, Grafana)
* Uses a custom network driver

### Grafana
* Configured with default settings, including the ability to connect to data sources like Prometheus
* Data persistence enabled via Docker volumes

### Seq
* Provides structured log data management
* Exposed on port `5341`

### ClickHouse
* A fast real-time analytical database
* Exposed on port `8123`

## Notes

* Modify the configurations in `docker-compose.yml` as per your specific requirements (e.g., ports, memory settings, security configurations)
* Make sure the necessary ports are available and not in use by other services on your system

## License

This repository is licensed under the MIT License. See the `LICENSE` file for more details.