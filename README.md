**Deployment Architecture and Release Process** 

This project adopts a container‑based deployment architecture that leverages managed AWS services to support reproducible builds, controlled releases, and scalable runtime orchestration. The application is packaged as a Docker container and built using AWS CodeBuild, which functions as the continuous integration mechanism. Successful builds generate immutable container images that are stored in Amazon Elastic Container Registry (ECR), ensuring consistency between build and deployment environments. 

Application execution and lifecycle management are handled through Amazon Elastic Kubernetes Service (EKS). Kubernetes Deployments provide mechanisms for replica management, health checking, and rolling updates, while Services establish stable network access for both the analytics application and the PostgreSQL database. Configuration details are externalized using ConfigMaps and Secrets, allowing environmental changes without rebuilding container images. 

Observability is implemented using AWS CloudWatch Container Insights, which captures runtime logs emitted by application containers. This enables monitoring of application behavior and verification of system health during execution. 

Releases are performed by updating application source code and triggering a new build through CodeBuild. A newly generated image is pushed to ECR and referenced by the Kubernetes Deployment, initiating a rolling update. This deployment model supports traceable, incremental releases while minimizing service disruption. 

## Deployment Architecture and Release Process

This project uses a container-based deployment workflow on AWS. The analytics application is packaged as a Docker image and built through AWS CodeBuild. Each successful build produces a container image that is pushed to Amazon Elastic Container Registry (ECR), which serves as the image repository for deployment.

The application is deployed to Amazon Elastic Kubernetes Service (EKS). Kubernetes Deployment resources manage pod creation, scaling, and rolling updates, while Kubernetes Services expose stable internal networking for both the analytics application and the PostgreSQL database. Configuration is separated from the container image through Kubernetes ConfigMaps and Secrets so that environment-specific values can be updated without rebuilding the application image.

Application observability is supported through AWS CloudWatch Container Insights, where container logs can be reviewed to confirm successful runtime behavior and troubleshoot issues.

## How to Release Changes

To release a new version of the application:
1. Update the application source code in the GitHub repository.
2. Push the changes to the repository connected to AWS CodeBuild.
3. CodeBuild rebuilds the Docker image and pushes the updated image to Amazon ECR.
4. Kubernetes pulls the updated image and applies the new version through a rolling deployment strategy.

These images help show that the application was built and deployed successfully and the application is actively producing logs in CloudWatch. 

<img width="1919" height="1199" alt="Screenshot 2026-03-31 001709" src="https://github.com/user-attachments/assets/883fa5a2-ef34-4ecc-968e-c9acf5e7c6e0" />
<img width="1911" height="692" alt="Screenshot 2026-03-31 002358" src="https://github.com/user-attachments/assets/4fd72744-c960-4b78-8848-8b4ee00a1f04" />
<img width="1910" height="1079" alt="Screenshot 2026-03-31 002024" src="https://github.com/user-attachments/assets/f2d0b79b-fe57-4b2b-9b60-70195644b39d" />
<img width="1913" height="1077" alt="Screenshot 2026-03-31 002047" src="https://github.com/user-attachments/assets/c0696aff-68ce-470a-a2f9-cb18d6aeaac2" />
<img width="1913" height="1077" alt="Screenshot 2026-03-31 002047" src="https://github.com/user-attachments/assets/c0696aff-68ce-470a-a2f9-cb18d6aeaac2" />
<img width="1909" height="1077" alt="Screenshot 2026-03-31 001922" src="https://github.com/user-attachments/assets/cf4573f6-5691-4131-b0cf-8be19a5b9db5" />
<img width="1916" height="1077" alt="Screenshot 2026-03-30 232846" src="https://github.com/user-attachments/assets/12f14adb-110c-4e40-8125-d7f9bdca4e83" />

<img width="920" height="498" alt="Screenshot 2026-03-31 000355" src="https://github.com/user-attachments/assets/053ee152-3e96-4025-aa46-ce0949f946e6" />
<img width="930" height="961" alt="Screenshot 2026-03-31 000332" src="https://github.com/user-attachments/assets/50e3d1b9-afde-4ed3-a31b-acb44f104d43" />
<img width="917" height="467" alt="Screenshot 2026-03-31 000225" src="https://github.com/user-attachments/assets/b1ad0082-6f15-45f8-9165-fdd9276a7d4b" />
<img width="922" height="469" alt="Screenshot 2026-03-31 000159" src="https://github.com/user-attachments/assets/1d3a510e-bc1f-42ab-bf94-5e089041d3c9" />
<img width="1453" height="223" alt="Screenshot 2026-03-30 235944" src="https://github.com/user-attachments/assets/86bb1e47-6588-4f11-b149-dfb09ce61d4b" />

<img width="1913" height="1075" alt="Screenshot 2026-03-31 004310" src="https://github.com/user-attachments/assets/dec76566-2714-4613-89b9-ac851db475a2" />
<img width="1913" height="1078" alt="Screenshot 2026-03-31 001425" src="https://github.com/user-attachments/assets/79129669-d043-46c7-8718-6c759b53fa81" />
