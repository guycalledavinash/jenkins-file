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








