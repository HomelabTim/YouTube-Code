# Install Yacht

```bash
docker volume create yacht
docker run -d -p 8001:8000 -p 9444:9443 --name yacht --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v yacht:/config selfhostedpro/yacht
```

# Login Info

```bash
admin@yacht.local
```
```bash
pass
```