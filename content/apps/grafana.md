# 📊 Grafana

> [!info]  
> **Grafana** is an open-source platform for monitoring and observability. It enables users to create dynamic dashboards to visualize and analyze data from a variety of sources such as [[Prometheus]], [[MySQL]], [[PostgreSQL]], and more.

🌐 **Project Homepage**: [Grafana](https://grafana.com/)  
📜 **Documentation**: [Grafana Docs](https://grafana.com/docs/grafana/latest/)

---

## 🔍 Overview

> [!info]  
> **Grafana** provides open-source tools for monitoring and observability. It allows you to create dynamic dashboards for visualizing and analyzing data across various data sources. Grafana integrates with services like [[Prometheus]], [[MySQL]], [[PostgreSQL]], and others.

### Why Use Grafana?

- **Data Visualization**: Powerful dashboard creation with support for multiple data sources.
    
- **Alerting**: Configure alerts based on data thresholds.
    
- **User Management**: Fine-grained access control for team-based monitoring.
    

---

## 🛠️ Features

> [!tip]  
> Grafana comes with many features to enhance monitoring and alerting capabilities:

- **Dashboards**: Create and share dashboards to visualize metrics and logs from various sources.
    
- **Data Source Integrations**: Supports a wide range of data sources including [[Prometheus]], [[MySQL]], [[PostgreSQL]], and more.
    
- **Alerting**: Configure alerts on data thresholds and monitor systems in real time.
    
- **Plugins**: Extend Grafana’s functionality with a rich library of plugins for panels, data sources, and apps.
    

🌍 **Explore More**: Learn more about Grafana's features on the [Grafana Docs](https://grafana.com/docs/).

---

## 🏃 Getting Started

### Step 1: Install Grafana

To install Grafana on your system, follow these commands for [[Ubuntu]]:

```bash
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo apt-get update
sudo apt-get install grafana
```

🌍 **Explore More**: For installation on other systems, check the [Grafana Installation Guide](https://grafana.com/docs/grafana/latest/installation/).

### Step 2: Start Grafana Service

Start Grafana as a service and enable it to run at startup:

```bash
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

🌍 **Explore More**: Grafana service management and troubleshooting can be found on the [Grafana Service Documentation](https://grafana.com/docs/grafana/latest/administration/).

### Step 3: Access the Dashboard

By default, Grafana runs on port `3000`. Open your browser and go to:

```
http://localhost:3000
```

Login using the default username `admin` and password `admin`.

🌍 **Explore More**: Learn more about accessing and configuring Grafana on the [Grafana UI Documentation](https://grafana.com/docs/grafana/latest/getting-started/).

---

## 🔧 Customization and Configuration

### Step 4: Add Data Sources

Grafana supports a variety of data sources. To add a data source:

1. Open Grafana and go to **Configuration** > **Data Sources**.
    
2. Select your data source (e.g., [[Prometheus]], [[MySQL]]).
    
3. Enter the necessary connection details and save the configuration.
    

🌍 **Explore More**: Learn more about configuring data sources on the [Grafana Data Sources Documentation](https://grafana.com/docs/grafana/latest/datasources/).

### Step 5: Create Dashboards

1. Click the **+** sign in the left sidebar and select **Dashboard**.
    
2. Click **Add Panel** to start creating visualizations using your data.
    
3. Customize the panel with the desired settings.
    

🌍 **Explore More**: For detailed instructions on creating dashboards, visit the [Grafana Dashboard Guide](https://grafana.com/docs/grafana/latest/dashboards/).

---

## 🔄 Related

- **[Prometheus Monitoring](https://prometheus.io/)** — Integrate Grafana with Prometheus to monitor systems.
    
- **[InfluxDB](https://www.influxdata.com/)** — Use InfluxDB as a time-series database with Grafana for real-time analytics.
    
- **[Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/)** — Integrate Grafana with Alertmanager for alerting and notification management.
    

---

## 🔗 Further Resources

For more information and advanced configurations, refer to the official Grafana documentation:

- [Grafana Homepage](https://grafana.com/)
    
- [Grafana Docs](https://grafana.com/docs/)
    

---

## 📚 Tags

- #Grafana
    
- #Dashboards
    
- #Monitoring
    
- #Alerting
    
- #Data-Visualization
    
- #Prometheus
    
- #MySQL
    
- #PostgreSQL
    