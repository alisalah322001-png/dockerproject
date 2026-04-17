# Docker Microservices 

This project demonstrates a simple microservices architecture using Docker with a custom network.

## 📦 Services

### Backend

* Python Flask application
* Runs on port 5000
* Built using Python base image
* Installs Flask

### Frontend

* Python application
* Uses requirements.txt for dependencies
* Runs on port 5000

## 🌐 Docker Network

A custom Docker network is created called:

ivolve-network

* Backend and frontend1 are connected to this network
* frontend2 runs on the default bridge network

## 🚀 How to Run

### 1. Build Docker Images

docker build -t backend-image ./backend
docker build -t frontend-image ./frontend

### 2. Create Network

docker network create ivolve-network

### 3. Run Backend Container

docker run -d --name backend --network ivolve-network backend-image

### 4. Run Frontend1 (Custom Network)

docker run -d --name frontend1 --network ivolve-network -p 5001:5000 frontend-image

### 5. Run Frontend2 (Default Network)

docker run -d --name frontend2 -p 5002:5000 frontend-image

## 🧪 Test Communication

docker exec -it frontend1 ping backend

* Works between containers in the same network
* Fails for containers in different networks

## 🧹 Cleanup

docker stop backend frontend1 frontend2
docker rm backend frontend1 frontend2
docker network rm ivolve-network

## 🧠 Key Concept

Containers in the same Docker network can communicate using container names as hostnames.

## 👨‍💻 Author

Ali
