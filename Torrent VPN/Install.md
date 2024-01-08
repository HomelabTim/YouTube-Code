# Docker Compose File

```bash
---
version: "2"
services:
  qbittorrentvpn:
    image: markusmcnugen/qbittorrentvpn
    container_name: qbittorrentvpn
    privileged: true   
    environment:
      - VPN_USERNAME= (YOUR INFO HERE)
      - VPN_PASSWORD= (YOUR INFO HERE)
      - VPN_ENABLED=yes
      - LAN_NETWORK=192.168.0.0/24 or 192.168.1.0/24
      - NAME_SERVERS=8.8.8.8,8.8.4.4
    ports:
      - 8080:8080
      - 8999:8999
      - 8999:8999/udp
    volumes:
      - /torrent/config/QBittorrentVPN:/config
      - /data/admin/Media/Downloads:/downloads
    restart: unless-stopped
```

# Change fstab

```bash
sudo nano /etc/fstab
```
```bash
//192.168.0.41/NAS /data cifs username=(YOUR INFO HERE),password=(YOUR INFO HERE) 0 0
```

```warning
DONT USE SNAP WITH DOCKER
```

if you do run this

```bash
sudo snap remove docker
sudo rm -R /var/lib/docker
sudo apt-get remove docker docker-engine docker.io
```