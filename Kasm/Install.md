
# how to set swap (No longer used)

```bash
sudo dd if=/dev/zero bs=1M count=5120 of=/mnt/5GiB.swap
sudo chmod 600 /mnt/5GiB.swap
sudo mkswap /mnt/5GiB.swap
sudo swapon /mnt/5GiB.swap
cat /proc/swaps 
echo '/mnt/5GiB.swap swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

# install Kasm

## create directories and set ownership

```bash
sudo mkdir -p /data/shares/development
sudo mkdir -p /data/profiles
sudo chown -R 1000:1000 /data
```

## download and extract kasm workspace

```bash
cd /tmp
curl -O https://kasmweb-build-artifacts.s3.amazonaws.com/kasm_backend/branches/develop/kasm_workspaces_develop.tar.gz
tar -xf kasm_workspaces_develop.tar.gz
sudo bash kasm_release/install.sh
```

# persistent profiles

```bash
/data/profiles/{username}

{
    "/data/shares/development": {
        "bind":"/shares",
        "mode":"rw",
        "uid":1000,
        "gid":1000,
        "required":false
    }
}
```

# chrome managed policies

```bash
/etc/opt/chrome/policies/managed/bookmarks.json

{
    "BookmarksBarEnabled": true,
    "ManagedBookmarks":[
        {
            "toplevel_name":"Managed Bookmarks"
        },
        {
            "name":"Kasm",
            "url":"www.kasmweb.com"
        }
    ]
}
```

# change the Docker run config override to this

```bash
{
    "hostname":"kasm",
    "user":"root",
    "environment" : {"START_PULSEAUDIO" : "0"}
}
```

# add this to Docker Exec Config (JSON) for sudo and root

```bash
{
 "first_launch":{
      "user":"root",
      "cmd":"bash -c 'apt-get update && apt-get install -y sudo && echo \"kasm-user  ALL=(ALL) NOPASSWD: ALL\" >> /etc/sudoers'"
  }
}
```

# code to connect to containers root profile

```bash
docker exec -it -u root (adminkasm.lo_9eea9be5) (<<changed per container) bash
```

# code for PPA in ubuntu for git

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
```