# Docker Engine Installation (+Docker compose) (Ubuntu 22.04 Jammy)


### Install engine
```bash
sudo apt -y update

sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu jammy stable"

apt-cache policy docker-ce

sudo apt install docker-ce

sudo systemctl status docker
```

### Manage user
```bash
sudo groupadd -f docker

sudo usermod -aG docker $USER

newgrp docker

groups
```

### Install Docker Compose

```bash
mkdir -p ~/.docker/cli-plugins/

curl -SL https://github.com/docker/compose/releases/download/v2.29.1/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose

chmod +x ~/.docker/cli-plugins/docker-compose
```

# Miniconda Installation

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh -b
source /home/$USER/miniconda3/bin/activate
conda init
```
