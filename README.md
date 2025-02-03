# InterSystems IRIS Monitoring with Prometheus and Grafana

This repository provides the necessary files to set up **monitoring for InterSystems IRIS** in Kubernetes using **Prometheus and Grafana**. It includes a **custom CSP page** for exposing additional IRIS metrics, a **Grafana dashboard**, and a **Prometheus configuration**.

## Contents
- **`dashboard.json`** – Pre-configured Grafana dashboard for IRIS metrics.
- **`custom-metrics.xml`** – CSP-based custom metrics endpoint for additional insights.
- **`values.yaml`** – Prometheus configuration for scraping IRIS metrics.

## Setup Instructions
1. **Deploy Prometheus & Grafana**  
   ```bash
   helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
   helm repo update
   helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring --create-namespace -f values.yaml
   ```

2. **Import Custom Metrics into IRIS**  
   - Import `custom-metrics.xml` via the **InterSystems Management Portal**.
   - Create a **web application** and configure `/metrics` as the CSP page.

3. **Update Prometheus Targets** (in `values.yaml`)  

4. **Import the Grafana Dashboard**  
   - Open **Grafana** and import `dashboard.json` via **Dashboards > Import**.
