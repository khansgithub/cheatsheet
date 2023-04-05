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
```
