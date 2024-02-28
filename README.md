Hey, let's see how to set up jenkins, configure various tools, build a pipeline out of it

# Preface
Jenkins is an open source CI/CD tool with good plugin integration
Runs on port 8080, enable this in security rules
Java is a pre-requisite

## Set up Jenkins
```
sudo apt update
sudo apt install default-jre
java -version
```
![java installed](https://github.com/guycalledavinash/jenkins-file/assets/90386560/b82f38ba-7d15-4ac6-86df-915a453cf7a9)

Install jenkins from [Source](https://www.jenkins.io/doc/book/installing/linux/)
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
```
jenkins -version
```
## Start Jenkins
To enable the Jenkins service to start
```
sudo systemctl enable jenkins
```
To start the Jenkins service
```
sudo systemctl start jenkins
```
To check the status whether its running 
```
sudo systemctl status jenkins
```
![status](https://github.com/guycalledavinash/jenkins-file/assets/90386560/fe083089-64cd-4290-af0e-649cbfe9292a)
Notice the end, it runs on port 8080, now let's allow the port in inbound traffic rules and access it
Initially, install the suggested plugins
![plugins](https://github.com/guycalledavinash/jenkins-file/assets/90386560/a5791a38-eb1f-4a69-8e01-7c6cf5966b18)
Setup new username, password, Done.

This is how the home page looks like:
![Home](https://github.com/guycalledavinash/jenkins-file/assets/90386560/508d118f-32f6-4168-a77c-2b65484c9ac1)

This is the 'Manage Jenkins', tab where we can edit, configure, install tools, etc
![manage](https://github.com/guycalledavinash/jenkins-file/assets/90386560/6592db24-940f-4dfb-bd2c-2a5d598a319c)

## Let's configure a VM as a slave
Switch to root and give permissions so that jenkins integration happens seamlessly 
```
sudo su
```
or switch back to normal user:
```
su ubuntu
```
create folder, give permissions, generate private and public keys:
```
sudo su
mkdir jenkins-slave
chmod 755 jenkins-slave
ssh-keygen
```
Copy that private key, paste in credentials tab on the jenkins server, this is for seamless authorization
![credentials](https://github.com/guycalledavinash/jenkins-file/assets/90386560/17b4b30d-4ae0-4f54-9b62-59d814e12322)
Go with SSH with private key
![ssh](https://github.com/guycalledavinash/jenkins-file/assets/90386560/63bb4130-7062-4c75-b1f7-eecd9cbf041a)


