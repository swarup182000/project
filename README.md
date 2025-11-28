# project


📦 CRUD-DD MEAN Stack – DevOps Deployment

This project contains the containerized MEAN (MongoDB, Express, Angular, Node.js) application deployed on AWS EC2 using Docker, Docker Compose, Nginx, and GitHub Actions CI/CD.

🚀 Tech Stack

Node.js (Backend – Express)

Angular (Frontend)

MongoDB (Database)

Docker & Docker Compose

GitHub Actions (CI/CD)

AWS EC2 Ubuntu

Nginx Reverse Proxy

🧩 Project Structure
crud-dd-task-mean-app/
├── backend/        # Node backend
├── frontend/       # Angular frontend
├── docker-compose.yml
└── .github/workflows/ci-cd.yml

🐳 Docker Setup
Backend Image

image: swarup98/crud-dd-task-backend-app:latest

Frontend Image

image: swarup98/crud-dd-task-frontend-app:latest

Build via CI/CD pipeline.

⚙️ Docker Compose

Runs all services:

docker-compose up -d


Services:

MongoDB

Backend (8080 internal)

Frontend (served via Nginx proxy)

🌐 Nginx Reverse Proxy (Port 80)

/etc/nginx/sites-available/default:

server {
    listen 80;

    location / {
        proxy_pass http://localhost:8081;
    }

    location /api/ {
        proxy_pass http://localhost:8080/;
    }
}


Restart:

sudo systemctl restart nginx

🔄 CI/CD – GitHub Actions

Workflow does:

Build backend image

Build frontend image

Push to Docker Hub

SSH into EC2

Run docker-compose pull

Restart containers

Trigger:

on:
  push:
    branches: [ main, master ]

🚀 Deployment (EC2)

Commands:

docker-compose pull
docker-compose up -d --remove-orphans
docker ps


App opens at:

http://52.66.102.246      # Frontend via Nginx
http://52.66.102.246:8081 /api # Backend API

👨‍💻 Author

Swarup Meshram
DevOps Engineer 
