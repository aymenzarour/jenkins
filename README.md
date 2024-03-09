# Nginx Deployment using Jenkins

## Project Overview

This project automates the deployment of an Nginx web server on Kubernetes using Jenkins. The repository contains files for Docker configuration, HTML and CSS code, Kubernetes deployment, and a Jenkins pipeline.

### Project Structure

nginx-deployment-using-jenkins
├── deploymentservice.yaml
├── Dockerfile
├── index.html
├── Jenkinsfile
├── nginx.conf
├── README.md
└── styles.css


### Docker Configuration (Dockerfile)

The `Dockerfile` is responsible for building the Nginx Docker image. It performs the following tasks:

- Uses the official Nginx base image.
- Removes the default Nginx configuration.
- Copies custom Nginx configuration (`nginx.conf`).
- Copies HTML (`index.html`) and CSS (`styles.css`) files to the Nginx web root.
- Exposes port 80.
- Starts Nginx in the foreground.

### HTML and CSS Code

The `index.html` and `styles.css` files define the content and styling for the Nginx web page. The HTML file includes a simple welcome message, while the CSS file provides basic styling.

### Kubernetes Deployment (deploymentservice.yaml)

The `deploymentservice.yaml` file contains Kubernetes configurations for deploying the Nginx container. It includes a Deployment, Service, and Ingress, defining the desired state of the application.

### Jenkins Pipeline (Jenkinsfile)

The `Jenkinsfile` defines the Jenkins pipeline that automates the entire deployment process. It consists of the following stages:

1. **Checkout Source:** Retrieves the source code from the GitHub repository.
2. **Build Image:** Builds the Docker image based on the specified Dockerfile.
3. **Pushing Image:** Pushes the Docker image to the Docker Hub registry.
4. **Deploying App to Kubernetes:** Applies the Kubernetes configurations to deploy the Nginx application.

### Getting Started

Follow these steps to set up and deploy the Nginx application using Jenkins:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/aymenzarour/nginx-deployment-using-jenkins.git

