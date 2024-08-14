after ubuntu instance created with t2.medium 

Install Java

sudo apt update
sudo apt install openjdk-17-jre
Verify Java is Installed

java -version
Now, you can proceed with installing Jenkins

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins


**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS.
Open port 8080 in the inbound traffic rules as show below.

EC2 > Instances > Click on
In the bottom tabs -> Click on Security
Security groups
Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed All traffic).

Login with Jenkins : instal docker pipeline and sonarqube scanner and thn restart later,

On the ubuntu : 
apt install unzip
sudo su 
adduser sonarqube
sudo su - sonarqube
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip
unzip *
chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424
chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424
cd sonarqube-9.4.0.54424/bin/linux-x86-64/
./sonar.sh start

http://18.207.156.102:9000/ 
admin
admin


now login to it go to settings and generate token copy it 
and go to -> manage jenkins-> credential -> system -> global credentials-> new credenta-> sceret text -> paste the token 

then ubuntu :
exit from sonar 
install docker :
sudo apt update
sudo apt install docker.io
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker


http://<ec2-instance-public-ip>:8080/restart

The docker agent configuration is now successful.
