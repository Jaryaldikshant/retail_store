# 📦 Catalog Service - AWS Retail Sample

This is a sample **Catalog Service** built with **Go**. It provides an API to retrieve product catalog information, stored in a **MySQL** database.

---

## 🛠️ Tech Stack

| Language | Persistence |
|----------|-------------|
| Go       | MySQL       |

---

## ⚙️ Configuration

You can use the following environment variables to configure the service:

| Variable Name                                 | Description                                                    | Default        |
|----------------------------------------------|----------------------------------------------------------------|----------------|
| `PORT`                                       | Port the service runs on                                       | `8080`         |
| `RETAIL_CATALOG_PERSISTENCE_PROVIDER`        | Use `in-memory` or `mysql` as the backend                      | `in-memory`    |
| `RETAIL_CATALOG_PERSISTENCE_ENDPOINT`        | MySQL database endpoint URL                                    | `""`           |
| `RETAIL_CATALOG_PERSISTENCE_DB_NAME`         | Name of the MySQL database                                     | `catalogdb`    |
| `RETAIL_CATALOG_PERSISTENCE_USER`            | MySQL user name                                                | `catalog_user` |
| `RETAIL_CATALOG_PERSISTENCE_PASSWORD`        | MySQL password                                                 | `""`           |
| `RETAIL_CATALOG_PERSISTENCE_CONNECT_TIMEOUT` | Connection timeout (in seconds)                                | `5`            |

---

## 🧪 Utility Endpoints (Chaos Testing)

You can simulate failures or delays using these endpoints:

| Method   | Endpoint                   | Description                                                   |
|----------|----------------------------|---------------------------------------------------------------|
| `POST`   | `/chaos/status/{code}`     | Forces all responses to return the specified status code      |
| `DELETE` | `/chaos/status`            | Resets status responses to normal                             |
| `POST`   | `/chaos/latency/{delay}`   | Adds a delay (in ms) to all responses                         |
| `DELETE` | `/chaos/latency`           | Removes the added delay                                       |
| `POST`   | `/chaos/health`            | Simulates a failed health check                               |
| `DELETE` | `/chaos/health`            | Resets health check to normal                                 |

---

## 🚀 Running the Service

### 🔹 Run Locally

> ⚠️ Make sure a MySQL instance is already running.

**Steps:**
```bash
go build -o main main.go
./main
