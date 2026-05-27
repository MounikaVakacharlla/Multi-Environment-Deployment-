# Multi-Environment-Deployment-
# CI/CD Pipeline – Multi-Environment Deployment

## Task Overview

This Task demonstrates a professional CI/CD pipeline using GitHub Actions with support for multi-environment deployment. The workflow automatically deploys the application to a staging environment for testing and, after manual approval, deploys it to the production environment.

The purpose of this project is to simulate a real-world DevOps workflow with controlled and secure releases.

---

# Technologies Used

- GitHub Actions
- Python 3.11
- Docker
- Pytest
- Git
- Ubuntu Runner

---

# Workflow Overview

The CI/CD pipeline performs the following stages automatically:

1. Build Application
2. Install Dependencies
3. Run Unit Tests
4. Build Docker Image
5. Deploy to Staging Environment
6. Run Smoke Tests
7. Manual Approval for Production
8. Deploy to Production
9. Send Email Notifications

---

# Workflow Trigger

The workflow runs automatically when code is pushed or a pull request is created for the `main` branch.


GitHub Actions Workflow Structure

The workflow contains two deployment jobs:

staging → Automatically deploys application to staging environment
production → Deploys application to production after approval
Staging Deployment

The staging deployment job performs the following actions:

Build Docker image
Start Docker container
Deploy application to staging environment
Run smoke tests
Verify application availability

If smoke tests fail, the workflow stops automatically.

Smoke Testing

Smoke testing is used to verify that the deployed application is functioning correctly in the staging environment before production deployment begins.

Example checks:

Application starts successfully
Container is running
API or application endpoint is reachable
Production Deployment

The production deployment job runs only after:

Staging deployment completes successfully
Manual approval is provided

This ensures safe and controlled production releases.

Manual Approval Gate

GitHub Environment Protection Rules are used to require approval before production deployment.

Environment Setup

Go to:

Repository → Settings → Environments

Create the following environments:

staging
production

Inside the production environment:

Add Required Reviewers
Save protection rules

The workflow pauses until approval is provided.

Configure Secrets for Both Environments

Separate GitHub Secrets are configured for staging and production environments.

Go to:

Repository → Settings → Secrets and Variables → Actions
Staging Secrets
Secret Name	Purpose
STAGING_KEY	Simulated staging deployment key
STAGING_ENV	Staging environment identifier
Production Secrets
Secret Name	Purpose
PROD_KEY	Simulated production deployment key
PROD_ENV	Production environment identifier
Purpose of Separate Secrets

Using separate secrets for staging and production helps to:

Improve deployment security
Isolate environment configurations
Prevent accidental production exposure
Simulate real-world DevOps practices
Manage environment-specific settings
Email Notifications

The workflow sends email notifications after pipeline execution.

Notification Purpose
Monitor CI/CD execution
Receive deployment updates
Identify failures quickly
Improve deployment visibility
Required Email Secrets
Secret Name	Purpose
EMAIL_USERNAME	Sender email
EMAIL_PASSWORD	Gmail App Password


///Pipeline Flow

Push Code
   ↓
Build & Test
   ↓
Deploy to Staging
   ↓
Smoke Test
   ↓
Manual Approval
   ↓
Deploy to Production
   ↓
Email Notification
Running the Workflow

Push changes to GitHub using:

git add .
git commit -m "Updated CI/CD pipeline"
git push origin main

The workflow automatically starts from GitHub Actions.

Verify Workflow Execution

Go to:

Repository → Actions

Verify the following stages:

Build Success
Test Success
Staging Deployment
Smoke Test
Approval Request
Production Deployment
Email Notification
Deliverables
Updated GitHub Actions workflow file
Successful staging deployment logs
Successful production deployment logs
Approval gate configuration
README documentation
Application Features

✔ Automatic deployment to staging on push/PR
✔ Manual approval required for production
✔ Separate secrets for staging and production
✔ Verified deployments in both environments

