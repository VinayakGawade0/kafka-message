# kafka-message

This repository provides Docker Compose configuration and scripts to stand up a Kafka messaging environment, including Zookeeper, Kafka broker, Schema Registry, and Kafka Magic UI. It is part of the larger Kafka Streams project.

---

## Prerequisites

- Docker (v20+) and Docker Compose (v1.29+)
- Java 17+ (for any local Spring Boot services, if used)

---

## Docker Setup & Commands

Make sure you have Docker (v20+) and Docker Compose (v1.29+) installed.

1. Stop and remove containers, networks, and volumes:
   ```bash
   docker-compose down -v
   ```
2. Start containers in detached mode (no rebuild):
   ```bash
   docker-compose up -d
   ```

### Advanced Commands

1. Stop and remove containers, volumes, and orphan containers:
   ```bash
   docker-compose down -v --remove-orphans
   ```
2. Rebuild images and start containers in detached mode:
   ```bash
   docker-compose up -d --build
   ```

---

## Kafka Testing Commands

Once your Docker environment is up, you can test Kafka directly from the Kafka container:

1. **Create a topic**

   ```bash
   docker exec kafka kafka-topics --create --topic test-topic --bootstrap-server kafka:9092 --partitions 1 --replication-factor 1
   ```

2. **Produce a message**

   ```bash
   docker exec -i kafka kafka-console-producer --broker-list kafka:9092 --topic test-topic
   {"name":"test-user","message":"Hello Kafka!"}
   ```

3. **Consume messages**

   ```bash
   docker exec kafka kafka-console-consumer --bootstrap-server kafka:9092 --topic test-topic --from-beginning --timeout-ms 5000
   ```

---

## 📝 License

This project is licensed under the MIT License © Vinayak Gawade.
