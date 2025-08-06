# 🛒 Cart Service - AWS Retail Sample

This is a sample **Cart Service** built with **Java**. It stores customer shopping cart data using **Amazon DynamoDB**.

---

## 📦 Tech Stack

| Language | Persistence     |
|----------|------------------|
| Java     | Amazon DynamoDB |

---

## 🔧 Configuration

Set the following environment variables to configure the service:

| Variable Name                                     | Description                                                    | Default      |
|--------------------------------------------------|----------------------------------------------------------------|--------------|
| `PORT`                                           | Port the app listens on                                        | `8080`       |
| `RETAIL_CART_PERSISTENCE_PROVIDER`              | Storage option: `in-memory` or `dynamodb`                      | `in-memory`  |
| `RETAIL_CART_PERSISTENCE_DYNAMODB_TABLE_NAME`   | DynamoDB table name                                            | `Items`      |
| `RETAIL_CART_PERSISTENCE_DYNAMODB_ENDPOINT`     | Custom DynamoDB endpoint (optional)                            | `""`         |
| `RETAIL_CART_PERSISTENCE_DYNAMODB_CREATE_TABLE` | Set to `true` to auto-create DynamoDB table                    | `false`      |

---

## ⚙️ Utility Endpoints (Chaos Testing)

Useful endpoints to simulate delays, status codes, or health check failures:

| Method   | Endpoint                   | Description                                                   |
|----------|----------------------------|---------------------------------------------------------------|
| `POST`   | `/chaos/status/{code}`     | Forces all requests to return the given HTTP status code      |
| `DELETE` | `/chaos/status`            | Disables forced status code                                   |
| `POST`   | `/chaos/latency/{delay}`   | Adds delay (in ms) to all responses                           |
| `DELETE` | `/chaos/latency`           | Removes the artificial delay                                  |
| `POST`   | `/chaos/health`            | Causes health checks to fail                                  |
| `DELETE` | `/chaos/health`            | Restores normal health check behavior                         |

---

## ▶️ Running the Service

### 🔹 Run Locally

**Requirements:**
- Java 21

**Steps:**
```bash
./mvnw spring-boot:run
