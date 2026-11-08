# Elevate Labs – DevOps Internship

## Overview
This repository documents my hands-on learning and practical implementations during my DevOps Internship at Elevate Labs.

The repository contains daily internship tasks, source code, configuration files, documentation, and execution screenshots covering various DevOps concepts and tools.

## Technologies & Tools
- Git and GitHub
- GitHub Actions
- CI/CD Pipelines
- Node.js
- Docker
- DockerHub
- YAML
- PowerShell

## Internship Tasks

| Task | Title | Status |
|---|---|---|
| Task 01 | Automate Code Deployment Using CI/CD Pipeline | Completed – Implementation |
| Task 02 | To be updated | Upcoming |
| Task 03 | To be updated | Upcoming |

## Repository Structure

```text
Elevate-Labs-DevOps-Internship/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── Task-01-CICD-Pipeline/
│   ├── app.js
│   ├── server.js
│   ├── app.test.js
│   ├── package.json
│   ├── package-lock.json
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── screenshots/
│   └── README.md
│
└── README.md
```

## Learning Objectives
- Understand DevOps principles and practices.
- Implement Continuous Integration and Continuous Deployment workflows.
- Automate software testing and Docker image building.
- Work with containerization using Docker.
- Use GitHub Actions for workflow automation.
- Understand version control and deployment automation.

## Author
Atharv Vyahalkar

## Note
This repository will be continuously updated as new internship tasks are completed.
=======
# Task 01 – Automate Code Deployment Using CI/CD Pipeline

## 1. Project Overview

This project implements an automated Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub Actions.

A sample Node.js web application is used to demonstrate automated testing, Docker image building, and publishing images to DockerHub.

Whenever code is pushed to the `main` branch, GitHub Actions automatically executes the configured workflow.

## 2. Objective

To understand and implement an automated CI/CD pipeline that:

- Integrates source code with GitHub.
- Executes automated application tests.
- Builds a Docker image.
- Authenticates securely with DockerHub.
- Publishes the Docker image automatically.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Node.js | Backend application |
| JavaScript | Application development |
| Git | Version control |
| GitHub | Source code repository |
| GitHub Actions | CI/CD automation |
| YAML | Workflow configuration |
| Docker | Application containerization |
| DockerHub | Docker image registry |

## 4. Project Structure

```text
Task-01-CICD-Pipeline/
│
├── app.js
├── server.js
├── app.test.js
├── package.json
├── package-lock.json
├── Dockerfile
├── .dockerignore
├── README.md
└── screenshots/
```

The GitHub Actions workflow is maintained at the root of the internship repository:

```text
.github/
└── workflows/
    └── main.yml
```

## 5. Application Development

A simple Node.js HTTP application was developed with two endpoints:

- `/` – Displays a welcome message.
- `/health` – Returns the application health status in JSON format.

### Install dependencies

```bash
npm install
```

### Run the application

```bash
npm start
```

Application URL:

```text
http://localhost:3000
```

Health endpoint:

```text
http://localhost:3000/health
```

## 6. Application Testing

Node.js built-in testing functionality was used to verify application behaviour.

The test cases validate:

1. Homepage response and welcome message.
2. Health endpoint response and status.

Execute tests using:

```bash
npm test
```

Both test cases should pass before the Docker image is published.

## 7. Docker Implementation

A Dockerfile was created to containerize the Node.js application.

The implementation uses:

- Node.js Alpine base image.
- Working directory configuration.
- Dependency installation using `npm ci`.
- Application file copying.
- Port exposure on 3000.
- Application startup using `npm start`.

### Build Docker image

```bash
docker build -t devops-node-app:v1 .
```

### Run Docker container

```bash
docker run -d -p 3000:3000 --name devops-container devops-node-app:v1
```

### Verify running containers

```bash
docker ps
```

### Verify Docker images

```bash
docker images
```

The application was tested through the browser after running inside the Docker container.

## 8. DockerHub Integration

DockerHub was used as the container image registry.

The Docker image was tagged and uploaded to a public DockerHub repository.

### Tag Docker image

```bash
docker tag devops-node-app:v1 YOUR_USERNAME/devops-node-app:v1
```

### Push image

```bash
docker push YOUR_USERNAME/devops-node-app:v1
```

Replace `YOUR_USERNAME` with the actual DockerHub username.

DockerHub Repository:

`https://hub.docker.com/r/YOUR_USERNAME/devops-node-app`

## 9. GitHub Actions CI/CD Pipeline

A GitHub Actions workflow was configured using:

`.github/workflows/main.yml`

The workflow is triggered automatically when changes are pushed to the `main` branch within the Task 1 folder or when the workflow file itself changes.

A manual workflow trigger is also configured.

### Pipeline execution sequence

1. Checkout repository – Retrieves the source code.
2. Setup Node.js – Configures the Node.js environment.
3. Install dependencies – Installs packages using `npm ci`.
4. Run tests – Executes automated test cases.
5. DockerHub login – Authenticates using GitHub repository secrets.
6. Build and push Docker image – Builds and publishes the image to DockerHub.

### GitHub Secrets

The following repository secrets were configured:

| Secret | Description |
|---|---|
| `DOCKERHUB_USERNAME` | DockerHub account username |
| `DOCKERHUB_TOKEN` | DockerHub access token |

These secrets allow GitHub Actions to authenticate securely without exposing credentials in the source code.

### Docker image tags

The workflow publishes two image tags:

- `latest` – Represents the latest published image.
- Git commit SHA – Identifies the specific source code revision used for the image.

## 10. Verification and Results

The CI/CD workflow was executed through GitHub Actions.

The implementation demonstrated:

- Successful repository checkout.
- Successful Node.js environment setup.
- Dependency installation.
- Automated application testing.
- DockerHub authentication.
- Docker image building and publishing.

The workflow execution was monitored through the GitHub Actions dashboard.

A subsequent application update was also used to test the automated workflow and identify and correct a test assertion mismatch.

## 11. Screenshots

Add actual screenshots of your implementation in the `screenshots/` directory.

| Screenshot | Description |
|---|---|
| `application-running.png` | Node.js application running in browser |
| `docker-build.png` | Successful Docker image build |
| `docker-container.png` | Running Docker container |
| `dockerhub-repository.png` | Published DockerHub image |
| `github-actions-success.png` | Successful CI/CD workflow |
| `github-actions-update.png` | Workflow execution after code update |

## 12. Key Learnings

Through this task, I gained practical understanding of:

- CI/CD concepts and automation.
- Git and GitHub version control.
- GitHub Actions workflows, jobs and steps.
- YAML workflow configuration.
- Node.js application testing.
- Docker images and containers.
- Dockerfile creation and image building.
- DockerHub integration.
- Secure credential management using GitHub Secrets.
- Identifying and resolving CI/CD pipeline failures.

## 13. Conclusion

This task provided practical exposure to automating the software integration and Docker image publishing process.

By integrating Node.js, GitHub Actions, Docker and DockerHub, an automated workflow was implemented to test application code, build container images and publish them to a container registry.

The project demonstrates the fundamentals of CI/CD automation and provides a foundation for exploring more advanced DevOps tools and deployment practices.

**Note:** This implementation automates Docker image publishing to DockerHub. Deployment to a public application hosting environment is outside the scope of this task.
>>>>>>> task1/master
