# CI/CD Pipeline with GitHub Actions, Docker & AWS EC2

## Project Overview

This project demonstrates an end-to-end CI/CD pipeline using GitHub Actions, Docker, Docker Hub, and AWS EC2.

Whenever code is pushed to the `main` branch, GitHub Actions automatically:

1. Builds a Docker image.
2. Pushes the image to Docker Hub.
3. Connects to the EC2 server using SSH.
4. Pulls the latest Docker image.
5. Stops and removes the existing container.
6. Deploys a new container with the updated application.

This automation eliminates manual deployments and ensures faster and more reliable releases.

---

## Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├── Build Docker Image
    ├── Push Image to Docker Hub
    └── SSH into EC2
            │
            ▼
       Docker Engine
            │
            ▼
      Application Container
```

---

## Technologies Used

* Git
* GitHub
* GitHub Actions
* Docker
* Docker Hub
* AWS EC2
* Linux (Ubuntu)

---

## Project Structure

```text
.
├── .github
│   └── workflows
│       └── deploy.yml
├── Dockerfile
├── app/
├── README.md
└── other project files
```

---

## CI/CD Workflow

### Continuous Integration (CI)

When code is pushed to the `main` branch:

* Source code is checked out.
* Docker image is built.
* Image build is validated.

### Continuous Deployment (CD)

After successful build:

* Docker image is pushed to Docker Hub.
* GitHub Actions connects to EC2.
* Existing container is removed.
* Latest image is pulled.
* New container is started automatically.

---

## GitHub Secrets Used

The following secrets are configured in GitHub:

| Secret Name     | Purpose                   |
| --------------- | ------------------------- |
| DOCKER_USERNAME | Docker Hub Username       |
| DOCKER_PASSWORD | Docker Hub Access Token   |
| EC2_HOST        | Public IP of EC2 Instance |
| EC2_USER        | SSH User                  |
| SSH_PRIVATE_KEY | EC2 Private Key           |

---

## GitHub Actions Workflow

Location:

```text
.github/workflows/deploy.yml
```

Workflow triggers automatically on:

```yaml
on:
  push:
    branches:
      - main
```

---

## Docker Commands Used

Build Image

```bash
docker build -t myapp .
```

Run Container

```bash
docker run -d -p 80:3000 myapp
```

View Running Containers

```bash
docker ps
```

Stop Container

```bash
docker stop myapp
```

Remove Container

```bash
docker rm myapp
```

---

## Deployment Verification

SSH into EC2:

```bash
ssh ubuntu@<EC2_PUBLIC_IP>
```

Verify running containers:

```bash
docker ps
```

Check application logs:

```bash
docker logs myapp
```

---

## Screenshots

### GitHub Actions Pipeline Success

Add screenshot here.

### Docker Hub Image

Add screenshot here.

### Running Container on EC2

Add screenshot here.

### Application Access Through Browser

Add screenshot here.

---

## Learning Outcomes

Through this project, I learned:

* CI/CD concepts and implementation
* GitHub Actions workflow automation
* Docker image creation and management
* Docker Hub integration
* AWS EC2 deployment
* SSH-based automated deployments
* Infrastructure automation practices

---

## Future Enhancements

* Add automated testing stage
* Implement rollback mechanism
* Integrate Nginx reverse proxy
* Configure HTTPS using SSL certificates
* Deploy using Kubernetes
* Add monitoring and logging

---

## Author

Achal Padol

GitHub: https://github.com/achalpadol
LinkedIn: www.linkedin.com/in/achal-padol
