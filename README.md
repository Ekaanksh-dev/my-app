# Two-Tier Web App with Docker & Jenkins CI/CD

A production-ready two-tier web application demonstrating containerization with Docker and automated deployment using Jenkins pipelines.

## 🏗️ Architecture
```
Browser
   ↓
Nginx (Frontend Container :80)
   ↓
Express API (Backend Container :3000)
```

- **Frontend and backend run in isolated Docker containers**
- **Containers communicate over a shared Docker bridge network**
- **Jenkins automates build, test, and deployment**

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML, CSS, JavaScript |
| Web Server | Nginx (Alpine) |
| Backend | Node.js, Express |
| Containerization | Docker, Docker Compose |
| CI/CD | Jenkins |
| Version Control | Git, GitHub |

## 📁 Project Structure
```
my-app/
├── frontend/
│   ├── Dockerfile        # Nginx serves static files
│   ├── index.html
│   └── style.css
├── backend/
│   ├── Dockerfile        # Node.js Express API
│   ├── server.js
│   └── package.json
├── docker-compose.yml    # Orchestrates both containers
├── Jenkinsfile           # CI/CD pipeline definition
└── README.md
```

## 🚀 Quick Start

### Prerequisites

- Docker & Docker Compose installed
- Git installed
- (Optional) Jenkins for CI/CD

### Run with Docker
```bash
# Clone the repository
git clone https://github.com/Ekaanksh-dev/my-app.git
cd my-app

# Build and start containers
docker compose up --build

# Access the application
# Frontend: http://localhost:80
# Backend API: http://localhost:3000
```

### Run without Docker (Development)
```bash
# Start backend
cd backend
npm install
node server.js

# Open frontend
# Simply open frontend/index.html in your browser
```

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/message` | Returns a JSON message from backend |

Example response:
```json
{
  "message": "Hello from the backend!"
}
```

## 🔄 Jenkins CI/CD Pipeline

The automated pipeline follows three stages:

1. **Clone** — Pulls latest code from GitHub repository
2. **Build** — Builds Docker images for frontend and backend
3. **Deploy** — Starts containers using Docker Compose

### Pipeline Trigger Flow
```
Code Push → GitHub Webhook → Jenkins Pipeline → Build Images → Deploy Containers
```

### Jenkinsfile Overview
```groovy
pipeline {
    agent any
    stages {
        stage('Clone') {
            // Pull code from GitHub
        }
        stage('Build') {
            // Build Docker images
        }
        stage('Deploy') {
            // Deploy with docker-compose
        }
    }
}
```

## 🐳 Docker Configuration

### Frontend (Nginx)
- Base image: `nginx:alpine`
- Serves static HTML/CSS/JS files
- Exposes port 80

### Backend (Node.js)
- Base image: `node:alpine`
- Runs Express API server
- Exposes port 3000

### Network
Both containers share a custom bridge network defined in `docker-compose.yml`, allowing them to communicate using service names.

## 📝 Development Notes

- The frontend makes API calls to `http://localhost:3000/api/message`
- CORS is configured in the backend to allow cross-origin requests
- Environment variables can be added to `docker-compose.yml` for configuration

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👤 Author

**Ekaanksh**
- GitHub: [@Ekaanksh-dev](https://github.com/Ekaanksh-dev)

---

⭐ Star this repo if you found it helpful!
