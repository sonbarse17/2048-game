Phase 1 : Creating a Jenkins Server
1. Navigate to AWS Conose > EC2 
2. Create a Instance 
  Name : Jenkins
  AMI : Amazon Linux 2
  Instance Type : t2.medium
  Security Group : Allow Port 80 , 8080 ,
  Storage : 25 GB
3. SSH into Your Jenkins Instance
4. Install jenkins On EC2 
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
5. Copy Jenkins Public Ip and Paste In your browser #<Your-Ip>:8080
6. paste password from sudo cat /var/lib/jenkins/secrets/initialAdminPassword
7. Create a Jenkins admin User


Phase 2: Configuring Jenkins Server




