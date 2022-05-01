# Continous Integration Pipeline

## Install Jenkins server

### Create an EC2 Instance

> Add inbound Rule for port 8080

![EC2](PBL-9/EC2.png)

### Install Java JDK

```bash
sudo apt update

sudo apt install default-jdk-headless
```

### Install Jenkins

```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update

sudo apt install jenkins

# Verify Jenkins is running
sudo systemctl status jenkins

# Retrieve Jenkins initial password
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

![Jenkins](PBL-9/InstallJenkins.png)

### Configure Jenkins

## Configure Jenkins To Retrieve Source Code From Github Using WebHooks

### Enable Webhook on the Github Repository

![Webhook](PBL-9/Addwebhook.png)

### Create a new Freestyle project on Jenkins

![Jen7](PBL-9/Jen7.png)

### Add Github Repository

![Jen8](PBL-9/Jen8.png)

### Build The Project

![Jen1](PBL-9/Jen1.png)

### Configure triggering the build from github and Post-Build-Actions to archive all the files

![Jen9](PBL-9/Jen9.png)

### Test the Configuration

> Make Some changes in the repository and commit to Github

![Jen2](PBL-9/Jen2.png)

## Configure Jenkins To Copy Files To NFS Server Over SSH

### Install "Publish-Over-SSH" Plugin

![Jen10](PBL-9/Jen10.png)

### Configure the project to copy artifacts over to NFS server

![Jen3](PBL-9/Jen3.png)

### Add Post-Build-Action to send all archive files to the NFS server

![Jen4](PBL-9/Jen4.png)

## Test The Configuration

![Jen6](PBL-9/Jen6.png)

### Check the Files in the NFS server

![Jen5](PBL-9/Jen5.png)

