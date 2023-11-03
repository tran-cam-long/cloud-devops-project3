# Coworking Space Service Extension
### 1. Create EKS
Requirements:
- Make sure that you have IAM role set up to create EKS
- A VPC with subnets (default VPC will do)

### 2. Configure a Database
Set up a Postgres database using a Helm Chart. Using port forward to run SQL files to initialize token and user data

### 3. Create a new repository on ECR 
Create a new ECR repository
Use Docker to build local image then push to ECR repository with your userID

### 4. Create CodeBuild to build and push the image to ECR
Related to Dockerfile, buildspec.yml
With webhook trigger set up, for each build, the pipeline will push image with a tag by the hash of the commit and update the latest tag 

### 5. Create service and deployment
Run kubectl apply command for each file:
- Deployment and services: `deployment\co-working-space-analytics.yaml`
- ConfigMap for un-security env: `deployment\db-configmap.yaml`
- Secret for security env: `deployment\db-secret.yaml`

### 5. Configuring CloudWatch Insights

### 6. Verify deployment