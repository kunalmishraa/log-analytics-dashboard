# 🔥 Real-Time Log Analytics Dashboard (Kibana-Lite)

> A production-ready, scalable **log ingestion + search + monitoring** system built with **Spring Boot, MongoDB, Elasticsearch & Redis**.  
> Think of it as a **lightweight alternative to Kibana**, suitable for microservices log analysis, debugging, and live observability.

---

## 🚀 Features

| Feature | Description |
|--------|-------------|
| **Log Ingestion API** | Push logs via REST (supports JSON + batch) |
| **Search & Filtering** | Query by keyword, level, service, timestamp, etc. |
| **Real-Time Live Tail** | View logs as they are generated (WebSocket/SSE) |
| **Aggregations & Metrics** | Level distribution, service activity, time histograms |
| **Alert Rules** | Trigger alerts based on spike patterns (e.g., ERROR > 100 in 5m) |
| **Scalable Storage** | MongoDB for raw logs, Elasticsearch for searching |
| **High-Performance Caching** | Redis for rate limiting + queue buffering |
| **Swagger UI** | Fully documented APIs |

---

## 🧱 Architecture



```mermaid
flowchart TD

    %% STYLE DEFINITIONS
    classDef service fill:#4f46e5,stroke:#1e1b4b,color:#ffffff,stroke-width:1px;
    classDef db fill:#0ea5e9,stroke:#0c4a6e,color:#ffffff,stroke-width:1px;
    classDef cache fill:#f59e0b,stroke:#92400e,color:#ffffff,stroke-width:1px;
    classDef analytics fill:#22c55e,stroke:#14532d,color:#ffffff,stroke-width:1px;
    classDef ui fill:#9333ea,stroke:#3b0764,color:#ffffff,stroke-width:1px;

    A[Client Services / Applications] -->|POST /logs| B[Spring Boot Ingest API]

    B --> C[(MongoDB - Raw Log Storage)]
    B --> D[(Redis Stream - Buffer & Rate Limit)]

    D --> E[Background Indexer]
    E --> F[(Elasticsearch - Search Index)]

    F --> G[Real-Time Dashboard / API UI]

    %% Apply styles
    class B,E service
    class C,F db
    class D cache
    class G ui





---

## 🛠 Tech Stack

| Layer | Technology |
|------|------------|
| Backend | Spring Boot 3, Java 21 |
| Database | MongoDB |
| Search Engine | Elasticsearch |
| Cache / Stream | Redis |
| Live Updates | WebSocket / SSE |
| API Docs | Springdoc OpenAPI |
| Packaging | Docker / Jar |

---

## 📦 Spring Initializr Dependencies

```text
Spring Web
Spring Data MongoDB
Spring Data Elasticsearch
Spring Data Redis
Spring Security
Spring WebSocket
Spring Boot Actuator
Lombok
Spring Boot DevTools (optional)
Spring Boot Starter Test (default)



Additionally added manually:

springdoc-openapi-starter-webmvc-ui

micrometer-registry-prometheus (optional)

Testcontainers (optional for integration tests)



🧪 API Endpoints (Preview)
Method	Endpoint	Description
POST	/api/logs	Ingest single or batch logs
GET	/api/search/logs	Search logs by filters & keywords
GET	/api/live/tail	Stream logs in real-time
POST	/api/alerts	Create an alert rule
GET	/api/alerts/events	View triggered alerts
GET	/swagger-ui.html	API documentation



🐳 Local Development with Docker
docker compose up -d


This starts:

MongoDB

Elasticsearch (single node mode)

Redis

📁 Project Structure
src/
 ├─ main/java/com/yourname/loganalytics
 │   ├─ ingest/       # Log ingestion endpoints
 │   ├─ pipeline/     # Redis stream consumer -> ES indexer
 │   ├─ search/       # Search & aggregations
 │   ├─ alerts/       # Alert rules + scheduler
 │   ├─ live/         # SSE/WebSocket live tail
 │   └─ config/       # ES/Mongo/Redis configs
 └─ resources/
     └─ application.yml

💡 Screenshots (Add Once UI is Done)
Dashboard	Live Tail
coming soon	coming soon
🌍 Why This Project Matters

Modern distributed systems generate massive logs.
Traditional log viewers are slow, non-searchable, or lack real-time capabilities.

This system provides:

Centralized logging

Fast, full-text search

Live observability

Alerting on anomalies

Perfect for: backend engineers, SREs, DevOps, microservice debugging.

🤝 Contributing

Contributions are welcome!

Fork the repo

Create a new branch

Submit a pull request 🚀

⭐ Show Support

If this project helps you, please star the repo — it motivates development!
And share it with another backend dev 😊

⭐️ Star → Fork → Use → Improve → PR

Author

Your Name
GitHub → https://github.com/kunalmishraa

LinkedIn → https://www.linkedin.com/in/kunal-mishra-cse/


---

If you'd like, I can now:  
✅ Generate **project folder structure**  
✅ Create **Elasticsearch index mapping**  
✅ Write **Log Ingest API code**  

Just say: **"start coding"** 👨‍💻🚀