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

# Install Postgresql

sudo apt update -y

sudo apt install postgresql postgresql-contrib

sudo systemctl start postgresql.service

sudo systemctl enable postgresql.service

tc/postgresql/15/main/

sudo su

nano postgresql.conf
        (เปิด host หมด ) แก้ listen_addresses = '*'
        (เปิดเฉพาะ host - โค้ดเรียก ip ไหนใช้อันนั้น) แก้ listen_addresses = 'localhost,192.168.60.33'

nano pg_hba.conf
        เติมบรรทัดสุดท้าย
        (เปิดหมด IP) host    all    all    0.0.0.0/0 md5
        (เปิดรับเฉพาะ client) host all    all    172.19.0.0/16    md5
        ** เอา subnet มาจาก docker inspect bcp_api_api_1 | grep "IPAddress"  เช่น 172.19.0.2 แปลงเป็น 172.19.0.0/16

systemctl restart postgresql

เช็ค port ด้วย
ss -nlt | grp 5432

เช็ค connection ด้วย
psql -h 192.168.60.33 -p 5432 -d postgres -U postgres

exit ออกจาก su

ลง postgis ด้วย
sudo apt install postgis postgresql-15-postgis-3

ลองต่อ pgadmin แล้ว สร้าง db แล้ว create extension postgis;
