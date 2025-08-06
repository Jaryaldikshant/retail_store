# 🖥️ UI Service - AWS Retail Sample

This is the **frontend service** for the AWS Retail Sample application. It serves the HTML user interface and acts as a gateway that aggregates calls to the backend API services (catalog, cart, orders, checkout).

---

## 🛠️ Tech Stack

| Language | Persistence |
|----------|-------------|
| Java     | N/A         |

---

## ⚙️ Configuration

Configure the service using the environment variables below:

| Variable Name                          | Description                                                                 | Default                  |
|----------------------------------------|-----------------------------------------------------------------------------|--------------------------|
| `PORT`                                 | Port the service listens on                                                 | `8080`                   |
| `RETAIL_UI_THEME`                      | UI theme: `default`, `green`, `orange`                                     | `default`                |
| `RETAIL_UI_DISABLE_DEMO_WARNINGS`      | Set to `true` to hide demo warning banners                                 | `false`                  |
| `RETAIL_UI_PRODUCT_IMAGES_PATH`        | Custom path for product images                                             |                          |
| `RETAIL_UI_ENDPOINTS_CATALOG`          | Catalog API endpoint (`false` to use mock)                                 | `false`                  |
| `RETAIL_UI_ENDPOINTS_CARTS`            | Carts API endpoint (`false` to use mock)                                   | `false`                  |
| `RETAIL_UI_ENDPOINTS_ORDERS`           | Orders API endpoint (`false` to use mock)                                  | `false`                  |
| `RETAIL_UI_ENDPOINTS_CHECKOUT`         | Checkout API endpoint (`false` to use mock)                                | `false`                  |
| `RETAIL_UI_CHAT_ENABLED`               | Enable chatbot UI                                                          | `false`                  |
| `RETAIL_UI_CHAT_PROVIDER`              | Chat provider: `bedrock`, `openai`, `mock`                                 | `""`                     |
| `RETAIL_UI_CHAT_MODEL`                 | Model to use for chat                                                      | `""`                     |
| `RETAIL_UI_CHAT_TEMPERATURE`           | Model temperature                                                          | `0.6`                    |
| `RETAIL_UI_CHAT_MAX_TOKENS`            | Max response tokens for chat model                                         | `300`                    |
| `RETAIL_UI_CHAT_PROMPT`                | Chat model prompt (system message)                                         | `(see source)`           |
| `RETAIL_UI_CHAT_BEDROCK_REGION`        | AWS region for Bedrock                                                     | `""`                     |
| `RETAIL_UI_CHAT_OPENAI_BASE_URL`       | OpenAI base URL                                                            | `http://localhost:8888`  |
| `RETAIL_UI_CHAT_OPENAI_API_KEY`        | API key for OpenAI                                                         | `""`                     |

---

## 🧪 Utility Endpoints

These endpoints help with diagnostics and testing:

| Method | Endpoint                        | Description                                                                 |
|--------|----------------------------------|-----------------------------------------------------------------------------|
| `GET`  | `/utility/status/{code}`        | Returns the specified HTTP status code                                      |
| `GET`  | `/utility/headers`              | Displays incoming request headers                                           |
| `GET`  | `/utility/panic`                | Simulates a crash by shutting down the app                                 |
| `POST` | `/utility/echo`                 | Echoes back the POST request payload                                       |
| `POST` | `/utility/store`                | Saves payload to file and returns its hash                                 |
| `GET`  | `/utility/store/{hash}`         | Retrieves stored payload by hash                                           |
| `GET`  | `/utility/stress/{iterations}`  | Stress test: consumes CPU for the given number of iterations                |

---

## 🚀 Running the Service

### 🔹 Run Locally

**Requirements:**
- Java 21

**Steps:**
```bash
./mvnw spring-boot:run
