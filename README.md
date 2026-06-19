# 🚀 Express + OpenTelemetry + Jaeger Tracing

This project demonstrates how to add **distributed tracing** to a Node.js Express application using **OpenTelemetry** and visualize traces in **Jaeger UI**.

---

## 📦 Tech Stack

- Node.js
- Express.js
- OpenTelemetry SDK
- OTLP HTTP Exporter
- Jaeger (All-in-one)

---

## 📁 Project Structure


project/
│── tracing.js # OpenTelemetry setup
│── server.js # Express server
│── package.json # Project dependencies & scripts
|── package-lock.json
|── docker-compose.yml


---

## 📄 package.json

```json
{
  "name": "package",
  "version": "1.0.0",
  "scripts": {
    "start": "node -r ./tracing.js server.js"
  },
  "dependencies": {
    "@opentelemetry/api": "^1.9.1",
    "@opentelemetry/auto-instrumentations-node": "^0.77.0",
    "@opentelemetry/exporter-trace-otlp-http": "^0.219.0",
    "@opentelemetry/sdk-node": "^0.219.0",
    "express": "^5.2.1"
  }
}
⚙️ Setup Instructions
1. Install dependencies
npm install
2. Run Jaeger (Docker)
docker run -d --name jaeger \
  -p 16686:16686 \
  -p 4318:4318 \
  -p 4317:4317 \
  jaegertracing/all-in-one:latest
3. Start the application
npm start
🌐 API Endpoints
Method	Endpoint	Description
GET	/	Hello World
GET	/users	Sample API response
📊 View Traces in Jaeger

👉 http://localhost:16686

Steps:

Select service: express-server
Click Find Traces
View request timelines and spans
🧠 How It Works
Express handles requests
OpenTelemetry auto-instruments Node.js
Traces are exported via OTLP (port 4318)
Jaeger collects and visualizes traces
🚨 Troubleshooting

If no traces appear:

Ensure Jaeger is running
Check port 4318
Hit API endpoints after starting app
Ensure service name is set in tracing config
🏁 Result

You should see:

Request traces in Jaeger UI
Express route spans
Latency breakdown per request
