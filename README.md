# Marzban-node

In order for the port to automatically change to the desired one, you need to add "PORT your_port" at the end of your inbound tag, for example: "VLESS TCP REALITY PORT 443"
⚠️ It is also very important to insert the port you specified in the "host settings" so that the port in the subscription is displayed correctly.

## Quick install
Updating the server
```bash
sudo apt-get update && sudo apt-get upgrade
```

Installing the necessary software
```bash
sudo apt install socat -y && sudo apt install curl socat -y && sudo apt install git -y
```

Cloning the repository
```bash
git clone https://github.com/SPomodor/Marzban-node-change-port Marzban-node
```

We enter the working folder of the node
```bash
cd Marzban-node
```

Installing Docker
```bash
sudo curl -fsSL https://get.docker.com | sh
```

Creating a folder where we will place our certificate
```bash
sudo mkdir -p /var/lib/marzban-node/
```

Copying the previously received key
```bash
sudo nano /var/lib/marzban-node/ssl_client_cert.pem
```

Editing the docker-compose.yml file
```bash
sudo nano docker-compose.yml
```
```
services:
  marzban-node:
    image: spomodor/marzban-node:latest
    restart: always
    network_mode: host

    volumes:
      - /var/lib/marzban-node:/var/lib/marzban-node

    environment:
      SSL_CLIENT_CERT_FILE: "/var/lib/marzban-node/ssl_client_cert.pem"
      SERVICE_PROTOCOL: rest
```

Building a docker
```bash
docker build -t spomodor/marzban-node:latest .
```

Launching the node
```bash
sudo docker compose up -d
```

To restart the node
```bash
cd ~/Marzban-node
docker compose down --remove-orphans; docker compose up -d
```
## Manual install
Read the setup guide here: https://gozargah.github.io/marzban/docs/marzban-node
