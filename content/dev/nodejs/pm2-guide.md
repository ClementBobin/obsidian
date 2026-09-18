---
tags:
- clustering
- deployment
- nodejs
- pm2
- process-manager
- scalability
---

# ⚡ PM2

> [!info]  
> **PM2** is a powerful process manager for Node.js applications that helps manage and monitor processes in production environments. It ensures that applications remain alive, can restart automatically if they crash, and provides insightful metrics on performance.

🌐 **Project Homepage**: [PM2 Homepage](https://pm2.keymetrics.io/)

---

## 🔍 Overview

> [!info]  
> **PM2** is a Node.js process manager designed to keep applications running smoothly, even in high-demand environments. It provides several features such as automatic restarts, clustering, monitoring, and more.

### Why Use PM2?

- **Automatic Restarts**: Keeps your applications running by automatically restarting crashed processes.
    
- **Load Balancing**: Supports clustering to distribute traffic across multiple instances.
    
- **Log Management**: Aggregates and manages logs efficiently.
    
- **Monitoring & Metrics**: Provides a built-in dashboard for real-time monitoring.
    
- **Process Scaling**: Easily scales applications across multiple CPU cores.
    
- **Deployment Workflow**: Simplifies application deployment with a built-in process for handling updates.
    

---

## 🛠️ Features

> [!tip]  
> PM2 offers an array of powerful features for Node.js applications:

- 🔄 **Automatic Restart**: Keeps apps alive by auto-restarting them on crashes.
    
- 🖥️ **Clustering**: Distributes traffic across multiple app instances.
    
- 📊 **Real-time Monitoring**: Dashboard for tracking application performance.
    
- 🔐 **Zero-Downtime Deployments**: Allows deployment without interrupting the service.
    
- ⚙️ **Custom Configuration**: Define apps with an ecosystem file.
    

---

## 🏃 Getting Started

### 🧑‍💻 Install PM2

To install PM2 globally, run:

```sh
npm install -g pm2
```

To verify installation:

```sh
npm list -g pm2
```

---

## 🔧 Basic Usage

### Start an Application

```sh
pm2 start app.js
```

This starts the `app.js` file as a PM2-managed process.

### List Running Processes

```sh
pm2 list
```

Shows a table with information about all managed processes.

### Restart a Process

```sh
pm2 restart app
```

Restarts the process named `app`.

### Stop and Delete a Process

```sh
pm2 stop app
pm2 delete app
```

Stops and removes the process from PM2.

### Auto Restart on System Boot

> [!tip]  
> To ensure PM2 restarts applications when the system reboots, run:

```sh
pm2 startup
```

Then follow the instructions to enable the startup script.

### Logs

To view logs in real-time:

```sh
pm2 logs
```

To filter logs for a specific process:

```sh
pm2 logs app
```

### Process Scaling

To start multiple instances of an application:

```sh
pm2 start app.js -i max
```

To specify the number of instances:

```sh
pm2 start app.js -i 4
```

### Monitoring

For real-time monitoring:

```sh
pm2 monit
```

---

## 🔄 Related

- **[[Node.js]]** — Platform for building scalable network applications, like PM2.
    
- **[[Docker]]** — Containerization platform used with PM2 for scalable deployments.
    
- **[[Nginx]]** — Web server and reverse proxy that can work alongside PM2 for load balancing.
    

---

## 🌍 Explore More

- 🌐 [PM2 Documentation](https://pm2.keymetrics.io/docs/usage/quick-start/)
    
- 🌐 [PM2 GitHub Repository](https://github.com/Unitech/pm2)
    