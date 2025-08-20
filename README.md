# 🚀 Traefik Copier Template

This repository provides a **[Copier](https://copier.readthedocs.io/)** template for setting up [Traefik](https://traefik.io/) as a reverse proxy using **Docker Compose**.  
It is designed to support both **local development** and **production deployment** with separate configuration files.

---

## ✨ Features

- 🗂 **Environment separation**
  - `docker-compose.common.yaml.j2` → shared configuration
  - `docker-compose.devel.yaml.j2` → development setup (local, no SSL)
  - `docker-compose.prod.yaml.j2` → production setup (with Let's Encrypt SSL)

- ⚙️ **Dynamic Traefik configuration**
  - `traefik/traefik.yml.j2` for base configuration
  - Ready to extend with dynamic rules

- 🛠 **Helper scripts**
  - `scripts/up.sh.j2` → start services
  - `scripts/down.sh.j2` → stop services

- 📦 **Copier template structure**
  - `copier.yml` defines template questions and variables
  - Project scaffolding is generated into a target folder

---

## 📋 Requirements

- 🐧 Linux / macOS (recommended)
- 🐳 [Docker](https://docs.docker.com/get-docker/)
- 📦 [Docker Compose](https://docs.docker.com/compose/)
- 📐 [Copier](https://copier.readthedocs.io/) (`pip install copier`)

---

## ▶️ Usage

1. **Generate a new project from this template**

   ```bash
   copier copy gh:your-org/traefik-copier-template my-traefik-project
   cd my-traefik-project
