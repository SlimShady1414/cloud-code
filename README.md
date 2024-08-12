# Cloud Code
This project provides a long-running code environment with isolated user workspaces. (basically a clone of repl.it lol).

## Tools, Libraries, and Technologies Used

- **Node.js** - **Kubernetes** - **Docker** - **Node-pty** - **TypeScript** - **Socket.io** - **AWS S3**

## Setup and Configuration

### 1. Clone the Repository

Begin by cloning the repository to your local machine:

```bash
git clone https://github.com/SlimShady1414/cloud-code.git
cd cloud-code
```

### 2. AWS S3 Configuration

Create a `.env` file in the root of the backend services (`init-service`, `runner-service`, etc.) with the following content:

```plaintext
S3_ACCESS_KEY=your-aws-access-key
S3_SECRET_KEY=your-aws-secret-key
S3_REGION=your-aws-region
COPY_DIRECTORY_PATH=/path/to/your/local/directory
```

### 3. Setup Kubernetes Cluster

Start your Kubernetes cluster using Minikube:

```bash
minikube start
```

### 4. Build and Deploy Services

#### Backend Services

Navigate to each backend service directory, install dependencies, and start the services:

```bash
# Init Service
cd backend/init-service
yarn install
yarn start

# Orchestrator Service
cd ../orchestrator-service
yarn install
yarn start

# Runner Service
cd ../runner-service
yarn install
yarn start
```

#### Frontend

Set up the frontend:

```bash
cd frontend
yarn install
yarn start
```

#### Deploying on Kubernetes

Apply the Kubernetes configurations:

```bash
kubectl apply -f backend/orchestrator-service/orchestration-service.yaml
kubectl apply -f kubernetes/ingress-controller.yml
```

### 5. Clean Up

To stop the services and clean up the Kubernetes resources, run the following commands:

```bash
kubectl delete -f backend/orchestrator-service/orchestration-service.yaml
kubectl delete -f kubernetes/ingress-controller.yml
```
