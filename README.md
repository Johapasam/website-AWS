This README provides steps to deploy a PHP-based User Information Form using AWS EC2, RDS, CodeDeploy, and CodePipeline.

Prerequisites

AWS Account with EC2, RDS, IAM, CodeDeploy, and CodePipeline enabled.
MySQL Workbench for database setup.
GitHub account for storing the code.
Steps

1. Create IAM Roles
EC2 Role
CodeDeploy Role
2. Launch EC2 Instance
Choose Amazon Linux 2 as the AMI.
Select an instance type like t2.micro (free tier).
Attach the IAM role created for EC2 to this instance.
Set up User Data for installing Apache, PHP, and configuring the server.
Configure a Security Group to allow HTTP (80) and SSH (22).
3. Set Up RDS MySQL Database
Create an RDS MySQL instance.
Configure the RDS Security Group to allow the EC2 instance to connect on port 3306.
Use MySQL Workbench to set up your database and tables for the user data form.
4. Prepare GitHub Repository
Create a new repository on GitHub for your PHP code.
Push the PHP files, including the form and necessary configuration files (e.g., appspec.yml).
5. Set Up CodeDeploy
Create a CodeDeploy Application and link it to your EC2 instance.
Define a Deployment Group that specifies which EC2 instance(s) the code will be deployed to.
Ensure the CodeDeploy role has the necessary permissions to access EC2 and deploy files.
6. Set Up CodePipeline
Source Stage: Use GitHub as the source provider to pull code from your repository.
Build Stage (Optional): You can use AWS CodeBuild if necessary for building the application.
Deploy Stage: Select CodeDeploy as the deployment provider to deploy the code to EC2 instances.
7. Deploy the Application
Trigger CodePipeline to deploy the latest version of the code from GitHub to EC2 using CodeDeploy.
Monitor the pipeline stages and check if the deployment succeeds.
8. Test the Application
After deployment, access the application via the EC2 instance's public IP address.
Verify that the user information form is working and can submit data to the RDS database.
License

MIT License.
