# Docker Torrent Fundamental

A comprehensive guide for installing Docker on Ubuntu/Debian systems and setting up torrent services.

## Installation Steps

### 1. Update System Packages

Update your package index and upgrade existing packages:

```bash
sudo apt update && sudo apt upgrade -yy && sudo apt install git curl vim -yy
```

### 2. Install Required Dependencies

Install necessary dependencies for Docker:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/Cangio/linux-utils/main/docker-install.sh)"
```

The script installs docker, docker-compose, create a "docker" folder in main user directory and add user to docker group.
Should be working, comes from a merge of script with debian and ubuntu with AI.

### 3. Verify Docker Installation

Check that Docker is installed correctly:

```bash
sudo docker --version
sudo docker run hello-world
```

### 4. Set Up Torrent Service

Create a directory for your torrent configuration:

```bash
mkdir -p ~/dockers/torrent
cd ~/dockers/torrent
```

### 5. Configure docker-compose.yml

Copy or create the `docker-compose.yml` file in your torrent-services directory and customize it according to your needs.

### 6. Start Torrent Services

Launch your torrent services using Docker Compose:

```bash
docker compose up -d
```
(-d is `detached`, running even when closing ssh connection)

### 7. Check Running Containers

Verify that your containers are running:

```bash
docker ps -a
```

### 8. Access Torrent Web UI

Access your torrent client's web interface (the specific port depends on your service configuration, typically configured as port mapping in docker-compose.yml, e.g., `http://localhost:8080`).

### 9. Manage Services

Useful commands for managing your services:

**Using Docker Compose V2 (plugin):**
```bash
# Stop services
docker compose down

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## Additional Resources

- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
