# 🚀 Dockerized Node.js + TypeScript Express App

This project demonstrates a simple Node.js backend application built with **TypeScript** and **Express**, fully containerized using **Docker** and ready for deployment to environments such as AWS EC2 or ECR.

---

# 📌 Project Overview

This application:

- Uses **Express** as the web framework
- Is written in **TypeScript**
- Runs on **Port 3000**
- Is fully containerized using **Docker**
- Supports external access via `0.0.0.0`
- Demonstrates production-ready Docker build workflow

---

# 🏗️ Application Architecture

```
Client (Browser / Postman)
        ↓
Docker Container
        ↓
Node.js (Express Server)
        ↓
Route Handler (GET "/")
        ↓
Response: "Hello from Docker + TypeScript 🚀"
```

---

# 📂 Project Structure

```
.
├── src/
│   └── index.ts
├── dist/                # Compiled JavaScript (after build)
├── package.json
├── tsconfig.json
├── Dockerfile
└── README.md
```

---

# 🧠 Application Flow

## 1️⃣ Server Initialization

```ts
const app = express();
const port = 3000;
```

Creates the Express application and defines the port.

---

## 2️⃣ Route Handling

```ts
app.get("/", (_req: Request, res: Response) => {
  res.send("Hello from Docker + TypeScript 🚀");
});
```

When a client sends:

```
GET http://localhost:3000/
```

The server responds with:

```
Hello from Docker + TypeScript 🚀
```

---

## 3️⃣ Server Startup

```ts
app.listen(port, "0.0.0.0", () => {
  console.log(`Server running on port ${port}`);
});
```

Using `"0.0.0.0"` ensures:

- The app is accessible outside the container
- It works correctly on EC2
- It supports Docker networking

---

# 🐳 Docker Configuration Explained

## Dockerfile

```dockerfile
# Use official Node 20 image
FROM node:20

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Build TypeScript
RUN npm run build

# Expose port
EXPOSE 3000

# Start the app
CMD ["npm", "start"]
```

---

## 🐳 Docker Build & Run Flow

### Step 1: Build Docker Image

```bash
docker build -t my-node-app .
```

### Step 2: Run Container

```bash
docker run -p 3000:3000 my-node-app
```

Now access:

```
http://localhost:3000
```

---

# 🔄 Container Workflow Explanation

1. Docker pulls Node 20 base image.
2. Sets `/app` as working directory.
3. Installs dependencies.
4. Copies source code.
5. Compiles TypeScript → JavaScript.
6. Exposes port 3000.
7. Runs the application.

---

# 🧩 Key Concepts Demonstrated

## ✅ TypeScript Backend Setup
- Type-safe request/response handling
- Compilation before execution

## ✅ Express Server Configuration
- Route definition
- Middleware-ready structure

## ✅ Docker Containerization
- Environment consistency
- Portable deployment
- Production-ready build process

## ✅ Network Binding
Using:
```
0.0.0.0
```
Allows:
- External connections
- EC2 deployment
- Container networking

---

# ☁️ Deployment Possibilities

This application can be deployed to:

- AWS EC2
- Amazon ECR + ECS
- Kubernetes
- Any cloud container platform

---

# 🛠️ Future Improvements

- Add environment variable support
- Add health check endpoint
- Add logging middleware
- Add CI/CD pipeline
- Add multi-stage Docker build
- Add unit tests

---

# 🎯 Summary

This project demonstrates:

- Backend development using TypeScript
- Express server architecture
- Docker-based containerization
- Cloud deployment readiness

It serves as a foundational example of building and containerizing a modern Node.js backend service.

---

⭐ Built with Node.js, TypeScript, Express, and Docker

---
# GitHub Link
- https://github.com/SrideviMR/Docker
