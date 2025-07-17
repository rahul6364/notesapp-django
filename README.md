
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
# 📝 NotesApp - Django CI/CD Pipeline with Jenkins & Docker

A fully automated Django Notes App project with a CI/CD pipeline using Jenkins, Docker Compose, and a shared library approach.

## 🔧 Tech Stack

- 🐍 Django (Backend)
- 🐳 Docker & Docker Compose
- ⚙️ Jenkins (Multi-Agent)
- 📦 Docker Hub
- 🧠 Jenkins Shared Libraries
- 📁 GitHub (SCM)

---

## 🚀 Features

- Automated code cloning from GitHub
- Dockerized Django, MySQL, and Nginx setup
- Jenkins CI/CD pipeline with multiple stages:
  - **Code Checkout**
  - **Build Docker Image**
  - **Push to Docker Hub**
  - **Deployment using Docker Compose**
- Jenkins Shared Libraries for reusable pipeline logic
- Multi-agent node setup for scalability

---

## 🖼️ Architecture

```mermaid
graph TD
    GitHub -->|Triggers| Jenkins
    Jenkins -->|Clones Repo| Agent_Node
    Agent_Node -->|Builds| Docker_Image
    Docker_Image --> DockerHub
    Jenkins -->|Deploy| Docker_Containers
    Docker_Containers -->|Run| Django_App
