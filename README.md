## Three-Tier Application with Docker Compose

This project demonstrates a basic three-tier application using Docker Compose, consisting of:
1. **Frontend**: An NGINX server serving an HTML form.
2. **Backend**: A PHP application for processing form submissions.
3. **Database**: A MySQL database for storing user data.

---

## Prerequisites

To set up this project on an **Ubuntu server**, make sure you have the following:

- **Ubuntu Server**: Running Ubuntu 20.04 or later.
- **Docker**: Installed for containerizing the application.
- **Docker Compose**: For managing multi-container Docker applications.
- **SSH Client**: For accessing the server remotely.

---

## Installation Instructions

### 1. Setup Ubuntu Server
If you don’t have an Ubuntu server, you can set up one either locally or via cloud providers (e.g., AWS EC2, DigitalOcean). Ensure your instance is running Ubuntu 20.04 or later.

### 2. Install Docker and Docker Compose
Connect to your Ubuntu server via SSH:

```bash
ssh -i .pem key path ubuntu@publicip

# Update package index
sudo apt update

# Install Docker
sudo apt install docker.io -y

# Start and enable Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Verify Docker installation
docker --version

# Download Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/v2.6.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# Set executable permissions
sudo chmod +x /usr/local/bin/docker-compose

# Verify Docker Compose installation
docker-compose --version

Clone this project repository to your server:
git clone <repository-url>
cd three-tier

Run the following command to build and start the application containers:
docker-compose up -d

Directory Structure

three-tier/
├── docker-compose.yml         # Docker Compose configuration file
├── html/
│   └── index.html             # Frontend HTML file
├── nginx/
│   ├── Dockerfile             # NGINX Dockerfile
│   └── nginx.conf             # NGINX configuration file
├── php/
│   └── Dockerfile             # PHP Dockerfile
├── app/
│   └── index.php              # Backend PHP script
└── initdb/
    └── init.sql               # Database initialization script


Check the status of the containers:
docker-compose ps 

Once the containers are up, open your browser and navigate to:
http://<your-server-ip>

To interact with the MySQL database running in the Docker container, you can execute:
docker exec -it mysql_db mysql -u root -p
Enter the MySQL root password (pass123) and interact with the user_data database.

