# Jenkins_demos
Jenkins projects, installation guide, and troubleshooting 

**Jenkins** <br>
Jenkins is an open-source automation server that helps with continuous integration and delivery of software projects. It allows developers to automate various stages of the software development process. <br>

**Installing Jenkins on centos7**

1. Update your system packages by running the command <br>
```sudo yum update -y```

2. Install Java Development Kit (JDK) if it's not already installed. Jenkins requires Java to run. You can install OpenJDK by running <br>
```sudo yum install java-11-openjdk -y ```

3. Add the Jenkins repository key: Execute the following command to import the repository key <br>
```sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key```

4. Add the Jenkins repository: Create a Jenkins repository file: ```sudo vi /etc/yum.repos.d/jenkins.repo``` and add the following content
```
[jenkins]
name=Jenkins
baseurl=https://pkg.jenkins.io/redhat-stable
gpgcheck=1

```

5. Install Jenkins: Run the command<br>
```sudo yum install jenkins -y```

6. Start and enable the Jenkins service
```
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

7. Configure firewall rules: Allow incoming traffic on port 8080 (default Jenkins port) and reload
```
sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent
sudo firewall-cmd --reload
```

8. Access Jenkins: Open a web browser and visit ```http://your_server_ip:8080``` and follow the onscreen instuctions. 
