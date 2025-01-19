# Student Performance Predicition End-to-End Machine Learning Project with AWS CI/CD

## Overview
This project demonstrates an end-to-end machine learning pipeline deployed using **AWS CI/CD**. The pipeline incorporates Docker for containerization and GitHub Actions for automated workflows, enabling a scalable and efficient deployment.

## Features
- End-to-end machine learning pipeline.
- Dockerized application for easy deployment.
- AWS EC2 as a self-hosted runner for GitHub Actions.
- Integrated CI/CD with GitHub workflows and AWS.
- Deployment and orchestration using AWS Elastic Container Registry (ECR).

## Prerequisites
1. **AWS Account** with the following services:
   - IAM User with necessary permissions.
   - ECR repository.
2. **Docker** installed locally or on your EC2 instance.
3. **Git** for version control.
4. **Python** (Version 3.8 or above).

## Setup Instructions

### Local Docker Setup
1. Update and upgrade the system (optional):
   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade
   ```
2. Install Docker:
   ```bash
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker $USER
   newgrp docker
   ```

### AWS EC2 Setup
1. Launch an EC2 instance and SSH into it.
2. Install Docker using the steps above.
3. Configure EC2 as a self-hosted runner for GitHub Actions:
   - Follow the GitHub documentation to set up self-hosted runners.

### GitHub Secrets Configuration
Set up the following secrets in your GitHub repository:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION` (e.g., `us-east-1`)
- `AWS_ECR_LOGIN_URI` 
- `ECR_REPOSITORY_NAME` (e.g., `simple-app`)

## Project Structure
```
AWS-CI-CD-Projects/
├── .github/            # GitHub workflows
├── artifacts/          # Pipeline artifacts
├── notebook/           # Jupyter notebooks
├── src/                # Source code
├── templates/          # HTML templates (if applicable)
├── app.py              # Main application file
├── Dockerfile          # Docker configuration
├── requirements.txt    # Python dependencies
├── setup.py            # Python package setup
├── README.md           # Project documentation
└── .gitignore          # Git ignore rules
```

## Running the Application
1. Build the Docker image:
   ```bash
   docker build -t simple-app .
   ```
2. Run the Docker container:
   ```bash
   docker run -p 5000:5000 simple-app
   ```
3. Access the application at `http://localhost:5000`.
