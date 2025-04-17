# Traffic Data Collection and Reporting IoT System

## Project Overview
This project is a comprehensive traffic monitoring and analysis system that collects real-time traffic data, processes it through a data pipeline, stores it in a database, and provides APIs and visualization interfaces for reporting and analysis.

## System Architecture
The system consists of the following components:

1. **Rust Traffic Simulator** - Generates synthetic traffic data to simulate real-world traffic patterns.
2. **Kafka Message Broker** - Provides a scalable message queue for processing the high volume of real-time traffic data.
3. **Traffic Data API** - Backend service that processes and exposes traffic data through RESTful endpoints.
4. **Traffic Data Visualization Interface** - Frontend dashboard for visualizing traffic patterns, alerts, and analytics.
5. **MongoDB** - Database for storing processed traffic data and analytics.

## Components

### Rust Traffic Simulator
A high-performance traffic simulator written in Rust that generates realistic traffic data including:
- Vehicle movements
- Traffic density
- Intersection statistics
- Sensor data

### Kafka Traffic Component
Responsible for the message queue architecture:
- Zookeeper for Kafka cluster management
- Kafka brokers for message handling
- Producers that ingest traffic data
- Consumers that process and store data in MongoDB

### Traffic Data API
A Node.js backend service that:
- Provides RESTful endpoints for accessing traffic data
- Handles real-time data streaming
- Processes traffic events and generates alerts
- Calculates risk analysis and metrics
- Serves data to the visualization frontend

### Traffic Data Visualization Interface
A Next.js web application that offers:
- Real-time traffic monitoring dashboard
- Historical data analysis
- Intersection status visualization
- Alert monitoring
- Risk assessment reporting
- Interactive traffic maps
- Sensor status monitoring

## Prerequisites
- Docker and Docker Compose
- Git

## Installation

1. Clone the repository with submodules:
```bash
git clone --recurse-submodules https://github.com/yourusername/traffic_data_collection_and_reporting_iot.git
cd traffic_data_collection_and_reporting_iot
```

2. If you've already cloned the repository without submodules, initialize and update them:
```bash
git submodule init
git submodule update
```

## Running the System

The entire system can be started using a single Docker Compose command:

```bash
docker-compose up -d
```

This will start all components in the correct order with proper networking between services.

## Service Access Points

Once the system is running, you can access the following interfaces:

- **Traffic Visualization Dashboard**: http://localhost:3000
- **Traffic Data API**: http://localhost:3001/api
- **Kafka UI** (if enabled): http://localhost:8080
- **MongoDB** (for direct database access): localhost:27017

## Component Documentation

For more detailed information about each component, refer to the individual README files in each submodule:

- [Rust Traffic Simulator](./Rust-Traffic-Simulator/README.md)
- [Kafka Traffic](./kafka-traffic/README.md)
- [Traffic Data API](./traffic-data-API/README.md)
- [Traffic Data Visualization Interface](./traffic-data-visualisation-interface/README.md)

## System Diagram

```
┌──────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                  │     │                 │     │                 │
│  Rust Traffic    │────▶│  Kafka Message  │────▶│  MongoDB        │
│  Simulator       │     │  Broker         │     │  Database       │
│                  │     │                 │     │                 │
└──────────────────┘     └─────────────────┘     └─────────────────┘
                                │                         │
                                │                         │
                                ▼                         ▼
                         ┌─────────────────┐     ┌─────────────────┐
                         │                 │     │                 │
                         │  Traffic Data   │◀───▶│  Visualization  │
                         │  API            │     │  Interface      │
                         │                 │     │                 │
                         └─────────────────┘     └─────────────────┘
```

## Troubleshooting

If you encounter issues:

1. Ensure all Docker containers are running:
   ```bash
   docker-compose ps
   ```

2. Check logs for specific services:
   ```bash
   docker-compose logs [service-name]
   ```

3. Restart a specific service:
   ```bash
   docker-compose restart [service-name]
   ```

4. Ensure Kafka topics are created properly:
   ```bash
   docker-compose exec kafka kafka-topics --list --bootstrap-server localhost:9092
   ```

## License

This project is licensed under the MIT License - see the LICENSE file for details.