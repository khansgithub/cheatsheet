# git

#### switch user and choose which shell to use
```bash
su -s /bin/bash git
```

# s6

#### list services
```bash
ls /run/service/
```

#### restart service
```bash
s6-svc -r /run/service/svc-openssh-server
```

# etc

#### get umask
```bash
stat -c %a foo.txt
```

# docker
#### get docker
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
sudo usermod -aG docker $USER
newgrp docker
```

# go

#### get go
```bash
# https://go.dev/doc/install
wget <tar_from_https://go.dev/doc/install>
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.20.3.linux-amd64.tar.gz
sudo ln -s /usr/local/go/bin/go /usr/bin/go
#sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.20.3.linux-amd64.tar.gz
```
