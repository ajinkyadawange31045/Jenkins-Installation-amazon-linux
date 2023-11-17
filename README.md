### Jenkins Installation using Amazon linux in AWS.

Launch the EC2 instance with 8080 port enable in the security group.
Connect to the server using Mobaxterm

Update the software package of the instance using the below command:
```bash
sudo yum update -y
```

Install java packages and remove the oldest version of java if any:
```bash
sudo yum install java
```
```bash
sudo yum remove java-1.7.0-openjdk
```

inorder to switch in the versions in java:
press the index number according to the version you want to select, as per my observation, jenkins is running well on java 17 version.
```bash
sudo /usr/sbin/alternatives --config java
```
Add the Jenkins repo using the following command:
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
```

Import a key file from Jenkins-CI to enable installation from the package:
```bash
sudo rpm — import https://pkg.jenkins.io/redhat/jenkins.io.key
```
```bash
sudo yum upgrade
```

Install Jenkins using the below command:
```bash
sudo yum install jenkins -y
```

Start and enable the Jenkins service:
```bash
sudo systemctl start jenkins
```
if it doesn't start, check for the java version, jenkins version, and search for their compatibility online and upgrade or downgrade the versions if required.
```bash
sudo systemctl enable jenkins
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

