Deploy to EC2 with GitHub Actions
This project demonstrates a CI/CD pipeline using GitHub Actions to deploy code to an Amazon EC2 instance. The workflow deploys files to the specified directory on the EC2 instance when changes are pushed to the main branch.

Table of Contents
Features
Prerequisites
File Structure
Workflow Details
Usage
Troubleshooting
Contributing
License
1. Features <a name="features"></a>
Checks for the target directory (/var/www/html/resume) on the EC2 instance and creates it if it doesn't exist.
Deploys files from this repository to the EC2 instance, replacing any existing files and removing those not present in the repo.
2. Prerequisites <a name="prerequisites"></a>
Amazon EC2 Instance: Ensure you have an EC2 instance running with SSH access enabled.
GitHub Secrets: Add the following secrets in your GitHub repository for secure access to the EC2 instance:
HOST_DNS: Public DNS or IP of your EC2 instance.
USERNAME: SSH username for the EC2 instance.
EC2_SSH_KEY: SSH private key for accessing the EC2 instance.
3. File Structure <a name="file-structure"></a>
.github/workflows/deploy.yml: The GitHub Actions workflow that defines the deployment steps.
Project Root: Holds all source files and assets for deployment to the EC2 instance.
4. Workflow Details <a name="workflow-details"></a>
The GitHub Actions workflow (deploy.yml) executes automatically on every push to the main branch. Here's a step-by-step breakdown of the workflow:

Step 1: Checkout Repository
Action: Uses actions/checkout@v2 to clone the repository into the GitHub Actions runner.
Step 2: Set up SSH and Check/Create Directory
Action: Uses appleboy/ssh-action@master to SSH into the EC2 instance.
Details: Checks for the resume directory at /var/www/html/; if not present, it creates it.
Step 3: Copy Files to EC2
Action: Uses appleboy/scp-action@master to transfer files from GitHub to the EC2 instance.
Options:
overwrite: true: Replaces existing files with those from the repository.
rm: true: Deletes any files on the server that are not present in the repository.
5. Usage <a name="usage"></a>
Push Changes to GitHub: Commit and push changes to the main branch of your repository.
Automatic Deployment: GitHub Actions will trigger and deploy your changes to the EC2 instance.
6. Troubleshooting <a name="troubleshooting"></a>
SSH Connection Errors: Ensure your EC2 security group allows SSH access from GitHub IPs, and that your SSH key in EC2_SSH_KEY is valid.
Permission Issues: Verify that the SSH user has write permissions for /var/www/html/resume.
7. Contributing <a name="contributing"></a>
Feel free to open issues or submit pull requests for improvements or additional functionality.

8. License <a name="license"></a>
This project is licensed under the MIT License.

This README provides a well-organized overview for setting up and using the GitHub Actions workflow to deploy to an EC2 instance. Let me know if you'd like any further customization!






