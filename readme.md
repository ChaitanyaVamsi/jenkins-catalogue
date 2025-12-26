## redhat jenkins setup - Master

sudo dnf install net-tools -y
sudo yum install -y git
curl -o /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
yum install fontconfig java-21-openjdk -y
yum install jenkins -y
systemctl daemon-reload
systemctl enable jenkins
systemctl start jenkins

## plugins

stage view
Pipeline Utility Steps

## agent - ubuntu

apt-get update
sudo apt update
sudo apt install -y git
apt install openjdk-21-jre-headless
apt install nodejs
apt install docker.io
