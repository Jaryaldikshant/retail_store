# 📦 Orders Service - AWS Retail Sample

This is a sample **Orders Service** built with **Java**. It provides an API to store customer orders, and uses **MySQL** as the default database.

---

## 🛠️ Tech Stack

| Language | Persistence |
|----------|-------------|
| Java     | MySQL       |

---

## ⚙️ Configuration

Use the following environment variables to configure the service:

| Variable Name                                 | Description                                                                           | Default       |
|----------------------------------------------|---------------------------------------------------------------------------------------|---------------|
| `PORT`                                       | Port the app runs on                                                                  | `8080`        |
| `RETAIL_CHECKOUT_PERSISTENCE_PROVIDER`       | Persistence provider: `in-memory` or `postgres`                                       | `in-memory`   |
| `RETAIL_ORDERS_PERSISTENCE_POSTGRES_ENDPOINT`| PostgreSQL database endpoint                                                          | `""`          |
| `RETAIL_ORDERS_PERSISTENCE_POSTGRES_NAME`    | PostgreSQL database name                                                              | `""`          |
| `RETAIL_ORDERS_PERSISTENCE_POSTGRES_USERNAME`| Username for PostgreSQL                                                               | `""`          |
| `RETAIL_ORDERS_PERSISTENCE_POSTGRES_PASSWORD`| Password for PostgreSQL                                                               | `""`          |
| `RETAIL_ORDERS_MESSAGING_PROVIDER`           | Messaging provider: `in-memory`, `sqs`, or `rabbitmq`                                 | `"in-memory"` |
| `RETAIL_ORDERS_MESSAGING_SQS_TOPIC`          | SQS topic name for event publishing (if using SQS)                                   | `""`          |
| `RETAIL_ORDERS_MESSAGING_RABBITMQ_ADDRESSES` | RabbitMQ host and port (format: `host:port`)                                          | `""`          |
| `RETAIL_ORDERS_MESSAGING_RABBITMQ_USERNAME`  | RabbitMQ username                                                                     | `""`          |
| `RETAIL_ORDERS_MESSAGING_RABBITMQ_PASSWORD`  | RabbitMQ password                                                                     | `""`          |

---

## 🧪 Utility Endpoints (Chaos Testing)

These are helpful for testing error and delay scenarios:

| Method   | Endpoint                   | Description                                                   |
|----------|----------------------------|---------------------------------------------------------------|
| `POST`   | `/chaos/status/{code}`     | Forces all responses to return the given HTTP status code     |
| `DELETE` | `/chaos/status`            | Restores default status behavior                              |
| `POST`   | `/chaos/latency/{delay}`   | Adds delay (in ms) to all responses                           |
| `DELETE` | `/chaos/latency`           | Removes the artificial delay                                  |
| `POST`   | `/chaos/health`            | Simulates failed health check                                 |
| `DELETE` | `/chaos/health`            | Restores normal health check behavior                         |

---

## 🚀 Running the Service

### 🔹 Run Locally

**Requirements:**
- Java 21 installed

**Steps:**
```bash
./mvnw
