# Install Wireguard

```bash
sudo apt install wireguard -y 
sudo nano /etc/wireguard/wg0.conf 
```

# Run the tunnel

>[!WARNING]
>This is for running it on Linux

```bash
sudo wg-quick up wg0 
sudo wg-quick down wg0 
```
>[!TIP]
>To show the connections use:
>sudo wg show