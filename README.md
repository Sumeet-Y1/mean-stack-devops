# MEAN Stack CRUD Application - DevOps Deployment

A full-stack CRUD application built with MongoDB, Express, Angular 15, and Node.js. Containerized with Docker and deployed on AWS EC2 with automated CI/CD using GitHub Actions.

## Tech Stack

- **Frontend:** Angular 15
- **Backend:** Node.js + Express
- **Database:** MongoDB
- **Containerization:** Docker + Docker Compose
- **CI/CD:** GitHub Actions
- **Reverse Proxy:** Nginx
- **Cloud:** AWS EC2 (Ubuntu 22.04)

## Project Structure
```
mean-stack-devops/
├── backend/
│   ├── Dockerfile
│   └── app/
├── frontend/
│   ├── Dockerfile
│   └── src/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── docker-compose.yml
├── nginx.conf
└── README.md
```

## Setup & Deployment Instructions

### Prerequisites
- Docker & Docker Compose installed on VM
- GitHub account
- Docker Hub account
- AWS EC2 Ubuntu instance

### 1. Clone the Repository
```bash
git clone https://github.com/Sumeet-Y1/mean-stack-devops.git
cd mean-stack-devops
```

### 2. Run with Docker Compose
```bash
docker-compose up -d
```

### 3. Access the Application
Open your browser and navigate to:
```
http://<your-vm-ip>
```

## CI/CD Pipeline

The GitHub Actions pipeline automatically:
1. Builds Docker images for frontend and backend
2. Pushes images to Docker Hub
3. SSHs into AWS EC2 VM
4. Pulls latest images and restarts containers

### Pipeline Triggers
- Automatically runs on every push to `main` branch

### GitHub Secrets Required
| Secret | Description |
|--------|-------------|
| `DOCKER_USERNAME` | Docker Hub username |
| `DOCKER_PASSWORD` | Docker Hub access token |
| `VM_HOST` | AWS EC2 public IP |
| `VM_USER` | VM username (ubuntu) |
| `VM_SSH_KEY` | EC2 private key (.pem) |

## Docker Images

- **Backend:** `sumeety21/mean-backend:latest`
- **Frontend:** `sumeety21/mean-frontend:latest`

## Infrastructure

- **Cloud:** AWS EC2
- **OS:** Ubuntu 22.04
- **Instance:** t2.micro (Free Tier)
- **Ports:** 80 (HTTP via Nginx)

