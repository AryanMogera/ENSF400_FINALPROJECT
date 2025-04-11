# Demo Application CI/CD Project


## Project Overview
This project implements a CI/CD pipeline for the [Demo application](https://github.com/7ep/demo), showcasing DevOps practices including Git workflows, containerization, and automated testing.

## Docker Hub Registry

Our Docker image is available on Docker Hub:
[https://hub.docker.com/r/aryanmogera/ensf_finalproject](https://hub.docker.com/r/aryanmogera/ensf_finalproject)

## Team Members
- Sheharyar
- Aryan Mogera
- Fauzaan

## Repository Structure

### Branch Strategy
We are following a feature branch workflow with the following branche structure:

| Branch | Purpose |
|--------|---------|
| `main` | Production branch - final, stable code only |
| `development` | Integration branch for testing features before production |
| `feature/dockerfile` | Docker configuration (merged to development) |
| `feature/sheharyar` | Sheharyar's working branch |
| `feature/aryan-mogera` | Aryan's working branch |
| `feature/fauzaan` | Fauzaan's working branch |

> **Note:** Currently the `development` branch is ahead of `main` as we're using it for initial testing. The `main` branch will be updated with stable, production-ready code after thorough testing.

## Git Workflow Process

1. All feature development happens in individual feature branches
2. Pull requests are created to merge features into the `development` branch
3. Pull requests require at least 2 reviews before merging
4. After testing in `development`, changes will be merged to `main`

## Docker Configuration

The application has been containerized and can be run with Docker locally:

```bash
# Build the Docker image
docker build -t yourusername/ensf_finalproject .

# Run the container
docker run -it -p 8080:8080 yourusername/ensf_finalproject
```

If pulling from the Docker Hub Registry use these commands:

```bash
# Build the Docker image
docker pull aryanmogera/ensf_finalproject:v1.0

# Run the container
docker run -it  -p 8080:8080 aryanmogera/ensf_finalproject:v1.0
```

Once running, the application can be accessed at: [http://localhost:8080/demo](http://localhost:8080/demo)

## CI/CD Pipeline with Jenkins
To automate the software development lifecycle, we implemented a complete CI/CD pipeline using Jenkins. This pipeline runs inside a GitHub Codespace using Docker and connects directly to our GitHub repository.

## GitHub Integration & Webhooks
We configured GitHub webhooks to automatically notify Jenkins of repository changes:

### Events triggered
- push
- pull_request
- create
- delete
  
Additionally, we connected Jenkins to GitHub using a Personal Access Token (PAT) with the following scopes:
- repo
- admin: repo_hook

## Jenkins Stages
Our Jenkinsfile defines the CI/CD process:
- Build – Compiles the application using Gradle
- Unit Tests – Runs test suites and publishes reports via junit
- Static Code Analysis – Scans code with SonarQube and enforces quality gates
- Security Analysis – Uses OWASP DependencyCheck
- Performance Testing – Executes JMeter tests
- Docker Build – Builds image tagged with commit hash
- Docker Push – Pushes image to Docker Hub
- Deploy to Test – Deploys to test environment when merged into main

## Project Status
- [x] GitHub repository setup
- [x] Git workflow implementation
- [x] Application containerization
- [x] Docker image published
- [x] Jenkins CI/CD pipeline automation
- [ ] Automated testing
- [x] SonarQube integration
- [x] Deployment automation
