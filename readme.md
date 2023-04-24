# git
#### switch user and choose which shell to use
```bash
su -s /bin/bash <user>
```
#### credential cache helper
```bash
git config --global credential.helper cache
git config --local credential.helper cache

git config --global --unset credential.helper
```
#### disable credential helper for single command
```bash
git clone https://bitbucket.org/<repo>.git --config credential.helper=
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

# docker
#### get docker
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
sudo usermod -aG docker $USER
newgrp docker
```
#### list containers by name
```shell
docker ps -a --format "{{.Names}}"
```
#### basic health check 
```shell
docker run \
    ...
    --health-cmd "set -e;  nc -zv localhost 22; if [ $? -eq 0 ]; then exit 0; else exit 1; fi" \
    --health-interval=10s 
    ...
```
### troubleshooting
#### Error response from daemon: client version 1.40 is too new...
```bash
# set to working version
DOCKER_API_VERSION=1.41
```
### etc
#### docker ps name and status format
```
docker ps --format "{{printf \"%-30s %-20s\" .Names .Status}}"
```
```
watch 'docker ps --format "{{printf \"%-30s %-20s\" .Names .Status}}"'
```

# python
#### interactive pdb
```python
import ipdb
ipdb.set_trace()
```
#### module structure
_https://ianhopkinson.org.uk/2022/02/understanding-setup-py-setup-cfg-and-pyproject-toml-in-python/_
```
├── README
├── pyproject.toml
├── setup.py
└── src
    └── foobar
        └── __init__.py
```
##### pyproject.toml
```
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"
```
##### setup.py
```python
#! /usr/bin/env python

from setuptools import setup

if __name__ == "__main__":
    setup()
```
#### install module develop mode
```bash
pip install --editable .
pip install -e .
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

# linux
#### list all listening ports and associated services
```bash
sudo netstat -tunlp
```
#### get umask
```bash
stat -c %a foo.txt
```

# tmux
#### basics
```
        new window - CTRL + b + c
     switch window - CTRL + b + [0-9]+
  vertical split | - CTRL + b + %
 horizonal split _ - CTRL + b + "
   navigate panels - CTRL + b + ↑ / ↓ / ← / →
```
### rename window / pane
#### window
```
CTRL + B + ,
```
#### pane
```
CTRL + B + :
select-pane -T <PANE NAME>
```

# redis
```
redis-cli
```
#### list keys
```
keys * 
```
#### read stream
```
xrange <key> - + 
```
#### find keys and pipe to delete
```
#             < query >
redis-cli keys rq:res* | awk '{print $1}' | xargs redis-cli del
```

# curl
#### pass file to curl as data
```
curl localhost:3000/workflow -X POST  -H 'Content-Type: application/json' --data-binary "@data.json"
```
