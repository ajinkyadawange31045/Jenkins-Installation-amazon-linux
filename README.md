### Jenkins Installation using Amazon linux in AWS.

Launch the EC2 instance with 8080 port enable in the security group.
Connect to the server using Mobaxterm

Update the software package of the instance using the below command:
```bash
sudo yum update -y
```

Install java packages and remove the oldest version of java if any:
```bash
sudo yum install java-1.8.0
```
```bash
sudo yum remove java-1.7.0-openjdk
```

Add the Jenkins repo using the following command:
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

Import a key file from Jenkins-CI to enable installation from the package:
```bash
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```
```bash
sudo dnf upgrade
```

Install Jenkins using the below command:
```bash
sudo dnf install jenkins
sudo systemctl daemon-reload
```

Start and enable the Jenkins service:
```bash
sudo systemctl enable jenkins
```
```bash
sudo systemctl start jenkins
````

You can check the status of the Jenkins service using the command:
```bash
sudo systemctl status jenkins
```
Connect to http://<your_server_public_DNS>:8080 from your browser. You will be able to access Jenkins through its management interface:
Copy the path and get the password from the server:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Install the suggested plugins.
Add the user credentials and save it.

Installation and configuration are completed and now you can start creating the Jenkins jobs.

Source - https://www.jenkins.io/doc/book/installing/linux/#fedora
