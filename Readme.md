Phase 1 : Creating a Jenkins Server
1. Navigate to AWS Conose > EC2 
2. Create a Instance 
  Name : Jenkins
  AMI : Amazon Linux 2
  Instance Type : t2.medium
  Security Group : Allow Port 80 , 8080 ,
  Storage : 25 GB
3. SSH into Your Jenkins Instance
4. Install jenkins and Docker On EC2
   Jenkins Installation
```
    #!/bin/bash
    sudo yum update –y
    sudo wget -O /etc/yum.repos.d/jenkins.repo \
        https://pkg.jenkins.io/redhat-stable/jenkins.repo
    
    sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
    sudo yum upgrade
    sudo dnf install java-21-amazon-corretto -y
    sudo yum install jenkins -y
    sudo systemctl enable jenkins
    sudo systemctl start jenkins
    sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    # default port : 8080
```
  Docker Installation
```
    #!/bin/bash
    
    # Update the system packages
    sudo yum update -y
    
    # Install Docker
    sudo yum install -y docker
    
    # Start Docker service
    sudo systemctl start docker
    sudo systemctl enable docker
    
    # Add current user to docker group to run docker without sudo
    sudo usermod -aG docker $USER
    sudo usermod -aG docker jenkins
    newgrp docker
    
    # Change Docker socket permissions
    sudo chmod 777 /var/run/docker.sock
```
5. Copy Jenkins Public Ip and Paste In your browser #<Your-Ip>:8080
6. paste password from sudo cat /var/lib/jenkins/secrets/initialAdminPassword
7. Create a Jenkins admin User


Phase 2: Configuring Jenkins Server
1. Navigate to Manage Jenkins > Plugins > Available plugins
2. Install Snyk Security Plugin
3. Navigate to Manage Jenkins > Tools
4. Snyk Installations
   Name : snyk
   Install automaticy from Installer Latest version
5. Apply and save Configuration
6. Get Your Snyk API Token from your snyk account
   - Navigate to your snyk account
   - Go to your account setting
   - Account > General > Auth Token
   - Copy Your API Token
7. Navigate to Manage Jenkins > Credentials
8. Create a Global credential
   - Kind : Snyk API Token
   - Token : <Your-Snyk-token>
   - ID : snyk-api-token
9.




