# Copier Template: Traefik Stack (Split Compose)

Template ini dibuat dari arsip yang Anda unggah. Menghasilkan struktur tiga file Compose:
- `docker-compose.common.yaml`
- `docker-compose.devel.yaml`
- `docker-compose.prod.yaml`

Serta konfigurasi Traefik:
- `traefik/traefik.yml`
- `traefik/dynamic/dynamic.yml`

## Cara pakai

1. Install copier:
   ```bash
   pipx install copier  # atau pip install copier
   ```

2. Buat project baru dari template ini:
   ```bash
   copier copy /path/ke/template/copier-traefik-template .
   ```

3. Jalankan di lokal (assume Anda pakai sudo docker):
   ```bash
   export COMPOSE_PROJECT_NAME="{'{'} stack_name {'}'}"
   sudo docker network ls | grep -q "{'{'} public_network {'}'}" || sudo docker network create "{'{'} public_network {'}'}"
   sudo docker network ls | grep -q "{'{'} internal_network {'}'}" || sudo docker network create "{'{'} internal_network {'}'}"
   sudo docker compose -f {'{'} project_slug {'}'}/docker-compose.common.yaml -f {'{'} project_slug {'}'}/docker-compose.devel.yaml up -d
   ```

4. Jalankan di production:
   ```bash
   export COMPOSE_PROJECT_NAME="{'{'} stack_name {'}'}"
   sudo docker network ls | grep -q "{'{'} public_network {'}'}" || sudo docker network create "{'{'} public_network {'}'}"
   sudo docker network ls | grep -q "{'{'} internal_network {'}'}" || sudo docker network create "{'{'} internal_network {'}'}"
   sudo docker compose -f {'{'} project_slug {'}'}/docker-compose.common.yaml -f {'{'} project_slug {'}'}/docker-compose.prod.yaml up -d
   ```

> Basic auth dashboard di production membutuhkan hash bcrypt. Gunakan salah satu:
> ```bash
> htpasswd -nbB {'{'} dashboard_user {'}'} 'PASSWORD' | cut -d: -f2
> openssl passwd -apr1 'PASSWORD'
> ```
> Lalu isikan ke `dashboard_password_hash` saat copier bertanya.

