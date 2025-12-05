# Observability Platform -- JConf Peru 2025

This project provides a complete **end‑to‑end observability platform**
using:

-   **OpenTelemetry Java Agent**
-   **OTel Collector**
-   **Grafana**
-   **Prometheus**
-   **Tempo**
-   **Loki**
-   **Demo Java Order Service**

It lets you collect **logs, metrics, and traces** from the demo Java
application and visualize them in the observability stack.

------------------------------------------------------------------------

# 🚀 1. Requirements

-   Docker & Docker Compose
-   Java 21+ (only if you run the service locally)
-   Git

------------------------------------------------------------------------

# 📦 2. Clone the Repository

``` bash
git clone https://github.com/jlgutman/observability-plattform-jconfperu2025.git
cd observability-plattform-jconfperu2025
```

------------------------------------------------------------------------

# 🛢 3. Start the Entire Observability Platform

The repository includes all services: Collector, Tempo, Loki,
Prometheus, and Grafana inside the **observability-plattform-jconfperu2025** docker‑compose.

Start everything:

``` bash
docker compose up -d
```

Check status:

``` bash
docker ps
```

You should see containers for: - grafana - prometheus - tempo - loki -
otel-collector

Also, this will build the order-service Docker image - Inject the
OpenTelemetry Java Agent (already configured in Dockerfile) - Export
traces, metrics, and logs to the **collector** container

Order service UI/API:

    http://localhost:8088

------------------------------------------------------------------------

# 📡 4. Validate Connectivity

## Check Collector Health:

    http://localhost:4318/v1/traces
    http://localhost:4318/v1/metrics
    http://localhost:4318/v1/logs

A POST request should return `200 OK` (GET returns 404 normally).

------------------------------------------------------------------------

# 📊 5. Access Grafana Dashboard

Grafana is available at:

    http://localhost:3000

Default credentials: - **user**: admin\
- **pass**: admin

### Dashboards:

-   **Tempo → Traces**
-   **Prometheus → Metrics explorer**
-   **Loki → Logs browser**

------------------------------------------------------------------------

# 🧪 6. Generate Test Traffic

Use the order-service endpoint:

``` bash
curl http://localhost:8088/orders/1
curl http://localhost:8088/orders/X
```

Or open the UI and click around.

Within a few seconds you should see in http://localhost:3000:

### In Grafana:

-   Traces in **Tempo**
-   Logs in **Loki**
-   Metrics in **Prometheus**

------------------------------------------------------------------------

# 🛠 7. Rebuild After Modifications

``` bash
docker compose build order-service
docker compose up -d
```

------------------------------------------------------------------------

# 🧹 8. Stop Everything

``` bash
docker compose down
```

------------------------------------------------------------------------

# ✅ Summary

This project provides a ready-to-run **observability platform** for Java
applications using OpenTelemetry.\
You can collect and visualize **traces, logs, and metrics** using a
single command.

* The llm-client-mcp-server-demo project was presented at the event.
It leverages telemetry data to provide contextual information
to an MCP server for AI agentic workflows. If you’d like a copy of the project,
feel free to let me know—I’d be happy to share it.

Enjoy hacking observability! 🎉
