
---

# 🧪 SonarQube Docker Setup with Caddy Reverse Proxy

This repository provides a minimal setup to run [SonarQube](https://www.sonarsource.com/products/sonarqube/) locally using Docker, with [Caddy](https://caddyserver.com/) as a reverse proxy for simplified access and optional HTTPS.

## 📦 Features

* Runs **SonarQube (LTS - Community Edition)** in a Docker container
* Uses **Caddy** as a reverse proxy (HTTP and HTTPS ready)
* Custom Docker network with static IPs
* Persistent volumes for SonarQube data, logs, and extensions

## 🚀 Quick Start

### Prerequisites

* [Docker](https://www.docker.com/)
* [Docker Compose](https://docs.docker.com/compose/)

### Clone the Repository

```bash
git clone https://github.com/your-username/sonarqube-docker-setup.git
cd sonarqube-docker-setup
```

### Start the Services

```bash
docker-compose up -d
```

Once the containers are up, access SonarQube at:

```
http://sonarqube.local
```

> ℹ️ Add `127.0.0.1 sonarqube.local` to your `/etc/hosts` file (or corresponding hosts file on Windows) to resolve the custom domain locally.

🔐 Default Credentials
Username: admin

Password: admin

You will be prompted to change the password on first login.

## 🛠 Configuration

### Docker Compose

* **SonarQube** runs on `172.18.4.2`, port `9000`
* **Caddy** listens on standard HTTP (80) and HTTPS (443) ports, forwarding requests to SonarQube

### Caddyfile

Example configuration (included in this repo) maps `http://sonarqube.loacl` to the SonarQube container.

```Caddyfile
sonarqube.local {
  reverse_proxy 172.18.4.2:9000
}
```

## 🗂 Directory Structure

```
.
├── docker-compose.yml
├── Caddyfile
└── README.md
```

## 📄 License

MIT


