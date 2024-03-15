## Overview:

The Vprofile GitOps project automates the deployment pipeline for a Java application using GitHub Actions, Docker, Maven, and Helm on Amazon EKS. It ensures code quality, builds Docker images, and deploys the application to Kubernetes. The project provides a streamlined CI/CD process for deploying Java applications to Kubernetes, enhancing development efficiency and reliability.

## Prerequisites:

- Access to an Amazon EKS Cluster: You should have access to an Amazon EKS cluster where you want to deploy the application. Ensure you have the necessary permissions to create resources in the cluster.

- Kubernetes Tools: You should have kubectl installed on your local machine to interact with the Kubernetes cluster.

- GitHub Repository: You should have a GitHub repository containing the source code of the Java application and the Kubernetes configuration files.

- AWS Credentials: If you are deploying to AWS services such as ECR or EKS, ensure you have AWS credentials configured on your local machine. You can set these up using the AWS CLI or environment variables.

- SonarCloud

- Docker (Optional): If you want to build Docker images locally before deploying to ECR, ensure you have Docker installed on your local machine. However, note that the project pulls the Docker image from Docker Hub in the Kubernetes deployment, so Docker is not required for deployment.

- Helm



## GitOps Workflow Overview

The GitOps workflow for the Vprofile project automates the deployment pipeline for a Java application to an Amazon EKS cluster. It leverages GitHub Actions for CI/CD, Docker for containerization, Maven for build automation, and Helm for Kubernetes deployment.

### Testing:

- The Testing job checks out the code from the GitHub repository and runs Maven tests to ensure the application functions as expected.
- It also performs code style checks using Checkstyle to maintain code quality standards.

### Build and Publish:

- The Build_And_Publish job builds the Docker image for the application and uploads it to the specified Amazon ECR repository.
- It tags the Docker image with the latest version and the GitHub run number for versioning.

### Deploy to EKS:

- The DeployToEKS job configures AWS credentials and retrieves the Kubernetes config file to access the EKS cluster.
- It deploys the application using Helm charts, pulling the Docker image from the ECR repository.
- The deployment includes setting up services, pods, and any necessary configurations for the application to run in the Kubernetes cluster.

### Accessing the Application:

- Once the deployment is complete, the application should be accessible at the specified service endpoints in the Kubernetes cluster.

### Continuous Integration and Delivery:

- The workflow is triggered on GitHub whenever there is a new commit or a manual trigger.
- It ensures that any changes to the codebase are tested, built, and deployed automatically, maintaining a continuous integration and delivery process.

This GitOps workflow streamlines the deployment process for the Vprofile application, ensuring consistent and reliable deployment to the Amazon EKS cluster.
