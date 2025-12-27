## sonarQube setup docker container

sudo apt update
sudo apt install docker.io

docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
docker run -d --name sonar -p 9000:9000 sonarqube:community

## jenkins - setup ubuntu

- jenkins needs java
  apt update
  apt install openjdk-21-jre-headless

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
 https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
 https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
 /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
