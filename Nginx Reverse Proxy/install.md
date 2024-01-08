# Add Directories

```bash
cd /
sudo mkdir nginx
sudo mkdir data
sudo mkdir letsencrypt
```
# Create Docker

```bash
cd nginx 
sudo nano docker-compose.yml
```
```bash
version: '2'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```
# Run Docker Image

```bash
docker-compose up -d 
```
# Login Info

```bash
Email:    admin@example.com
Password: changeme
```