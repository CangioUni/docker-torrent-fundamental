# docker-torrent-fundamental

A comprehensive guide for installing Docker on Ubuntu/Debian systems and setting up torrent services.

## Prerequisites

- Ubuntu/Debian-based system
- sudo privileges
- Internet connection

## Installation Steps

### 1. Update System Packages

Update your package index and upgrade existing packages:

```bash
sudo apt update
sudo apt upgrade -y
```

### 2. Install Required Dependencies

Install necessary dependencies for Docker:

```bash
sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

### 3. Add Docker's Official GPG Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

For Debian:
```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### 4. Set Up the Stable Repository

For Ubuntu:
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

For Debian:
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 5. Install Docker Engine

Update the package index and install Docker:

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

### 6. Verify Docker Installation

Check that Docker is installed correctly:

```bash
sudo docker --version
sudo docker run hello-world
```

### 7. Add Your User to the Docker Group (Optional)

To run Docker commands without sudo:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

### 8. Install Docker Compose

Download and install Docker Compose:

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### 9. Verify Docker Compose Installation

```bash
docker-compose --version
```

### 10. Set Up Torrent Service

Create a directory for your torrent configuration:

```bash
mkdir -p ~/torrent-services
cd ~/torrent-services
```

### 11. Configure docker-compose.yml

Copy or create the `docker-compose.yml` file in your torrent-services directory and customize it according to your needs.

### 12. Start Torrent Services

Launch your torrent services using Docker Compose:

```bash
docker-compose up -d
```

### 13. Check Running Containers

Verify that your containers are running:

```bash
docker-compose ps
docker ps
```

### 14. Access Torrent Web UI

Access your torrent client's web interface (typically at `http://localhost:8080` or the configured port).

### 15. Manage Services

Useful commands for managing your services:

```bash
# Stop services
docker-compose down

# View logs
docker-compose logs -f

# Restart services
docker-compose restart

# Update containers
docker-compose pull
docker-compose up -d
```

## Troubleshooting

- If you encounter permission errors, ensure you've added your user to the docker group and logged out/in again
- Check logs with `docker-compose logs` for service-specific issues
- Ensure required ports are not already in use

## Additional Resources

- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)