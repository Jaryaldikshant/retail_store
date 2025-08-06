# 🛍️ Checkout Service - AWS Retail Sample

This is a sample **Checkout Service** built with **Node.js**. It stores customer checkout data using **Redis**.

---

## 🛠️ Tech Stack

| Language | Persistence |
|----------|-------------|
| Node.js  | Redis       |

---

## ⚙️ Configuration

You can customize the service using these environment variables:

| Variable Name                              | Description                                                              | Default      |
|-------------------------------------------|--------------------------------------------------------------------------|--------------|
| `PORT`                                     | Port the app runs on                                                     | `8080`       |
| `RETAIL_CHECKOUT_PERSISTENCE_PROVIDER`    | Storage option: `in-memory` or `redis`                                   | `in-memory`  |
| `RETAIL_CHECKOUT_PERSISTENCE_REDIS_URL`   | Redis server URL                                                         | `""`         |
| `RETAIL_CHECKOUT_ENDPOINTS_ORDERS`        | Orders API endpoint (uses mock if empty)                                 | `""`         |
| `RETAIL_CHECKOUT_SHIPPING_NAME_PREFIX`    | Prefix to apply to shipping option names                                 | `""`         |

---

## 🧪 Utility Endpoints (Chaos Testing)

You can simulate issues or delays using the following endpoints:

| Method   | Endpoint                   | Description                                                   |
|----------|----------------------------|---------------------------------------------------------------|
| `POST`   | `/chaos/status/{code}`     | Forces all responses to return the given HTTP status code     |
| `DELETE` | `/chaos/status`            | Resets to normal behavior                                     |
| `POST`   | `/chaos/latency/{delay}`   | Adds delay (in ms) to all responses                           |
| `DELETE` | `/chaos/latency`           | Removes the artificial delay                                  |
| `POST`   | `/chaos/health`            | Simulates a failed health check                               |
| `DELETE` | `/chaos/health`            | Restores normal health check behavior                         |

---

## 🚀 Running the Service

### 🔹 Run Locally

**Requirements:**
- Node.js 16 or higher

**Steps:**
```bash
yarn start
