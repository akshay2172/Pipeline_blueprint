# Pipeline Blueprint

> A full-stack MERN application that documents and demonstrates the conceptual CI/CD pipeline workflow with 5 key stages.

## 📋 Overview

**Pipeline Blueprint** is an educational project designed to help developers understand the CI/CD (Continuous Integration/Continuous Deployment) workflow. This is a **conceptual project** that documents the different stages of a modern CI/CD pipeline, providing a reference guide for implementing automated build, test, and deployment processes.

While this project doesn't implement a live, working CI/CD system, it provides clear documentation and structure for learning about how CI/CD pipelines work and what each stage entails.

## 🎯 What Does This Project Do?

This project demonstrates the following **5 key CI/CD stages**:

### 1. **Trigger + Checkout**
- Triggered on every push to the `main` branch
- Automatically checks out the repository code at the pushed commit
- Prepares the environment for subsequent stages

### 2. **Install + Quality Checks**
- Installs dependencies for both backend and frontend
- Runs linting checks (ESLint)
- Executes unit tests (if available)
- Fails fast if any checks fail

### 3. **Build Application Artifacts**
- Builds the frontend using Vite (React + TypeScript)
- Builds the backend application
- Ensures React/Vite compiles successfully
- Runs optional backend smoke tests
- Cleans up build artifacts before containerization

### 4. **Build Docker Image(s)**
- Creates Docker images for both backend and frontend
- Tags images with `latest` and a unique version (Git commit SHA)
- Prepares images for containerized deployment

### 5. **Push Image(s) to Registry**
- Authenticates with a container registry (Docker Hub / GitHub Container Registry)
- Pushes built images to the registry
- Tags images so the deployment server can pull them

## 🏗️ Project Structure

```
project_mern/
├── backend/                    # Express.js + MongoDB API
│   ├── src/
│   │   ├── routes/            # API route handlers
│   │   ├── models/            # MongoDB schemas
│   │   ├── db.js              # Database connection
│   │   └── server.js          # Express app setup
│   ├── package.json
│   ├── Dockerfile
│   └── .dockerignore
├── frontend/                   # React + Vite UI
│   ├── src/
│   ├── package.json
│   ├── vite.config.js
│   ├── Dockerfile
│   └── .dockerignore
├── docker-compose.yml         # Multi-container orchestration
├── setup_environment.sh       # Bootstrap script
├── .gitignore
└── README.md
```

## 🛠️ Tech Stack

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **Dotenv** - Environment variable management
- **CORS** - Cross-origin resource sharing

### Frontend
- **React 19** - UI library
- **Vite** - Build tool and dev server
- **Axios** - HTTP client
- **TypeScript** - Type safety
- **ESLint** - Code linting

### DevOps & Deployment
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration
- **Git** - Version control

## 🚀 Getting Started

### Prerequisites
- Node.js >= 16.x
- npm or yarn
- Docker & Docker Compose (optional, for containerized setup)
- MongoDB (local or Atlas)

### Quick Start

#### Option A: Run Using Docker Compose (Recommended)

```bash
# Clone the repository
git clone <your-repo-url>
cd project_mern

# Run the setup script
bash setup_environment.sh

# Start all services
docker-compose up -d

# Services will be available at:
# Frontend: http://localhost:5173
# Backend: http://localhost:5000
```

#### Option B: Run Locally

```bash
# Install backend dependencies
cd backend
npm install

# Create .env file in backend/
echo "MONGO_URI=mongodb://localhost:27017/pipeline-blueprint" > .env
echo "PORT=5000" >> .env

# Start backend
npm run dev

# In a new terminal, install frontend dependencies
cd frontend
npm install

# Start frontend dev server
npm run dev

# Access the app at http://localhost:5173
```

## 📝 Environment Variables

### Backend (.env)
```
MONGO_URI=mongodb://localhost:27017/pipeline-blueprint
PORT=5000
NODE_ENV=development
```

### Frontend (.env)
```
VITE_API_URL=http://localhost:5000
```

## 📚 Available Scripts

### Backend
```bash
cd backend
npm run dev          # Start development server with nodemon
npm start            # Start production server
npm run build        # Build backend (if applicable)
```

### Frontend
```bash
cd frontend
npm run dev          # Start Vite dev server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

## 🐳 Docker Setup

This project includes Dockerfiles for both frontend and backend:

```bash
# Build images
docker-compose build

# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

## 📖 CI/CD Pipeline Explanation

The documentation explains what each stage does, but **does not implement an actual working CI/CD system**. To implement a real CI/CD pipeline, you would use:

- **GitHub Actions** - For GitHub repositories
- **GitLab CI** - For GitLab repositories
- **Jenkins** - Self-hosted CI/CD server
- **CircleCI** - Cloud-based CI/CD
- **Travis CI** - Continuous integration platform

Each of these tools would be configured with a workflow/pipeline file (e.g., `.github/workflows/ci-cd.yml`) to automate the 5 stages described in this project.

## 🎓 Learning Objectives

After exploring this project, you'll understand:

- ✅ What happens at each stage of a CI/CD pipeline
- ✅ How code flows from commit to deployment
- ✅ Why automated testing and builds are important
- ✅ How Docker containerization fits into CI/CD
- ✅ The structure of a full-stack MERN application
- ✅ How to set up a multi-container application with Docker Compose

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📧 Contact & Support

For questions or issues:
- Open an issue on GitHub
- Check existing documentation in the `docs/` folder
- Review the CI/CD stages documentation at the top of this README

---


**Happy Learning!** 🚀 

Remember: This is a conceptual project meant to educate about CI/CD workflows. For production use, implement actual CI/CD using the tools mentioned above.