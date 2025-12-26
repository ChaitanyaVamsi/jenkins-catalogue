## redhat jenkins setup - Master

curl -o /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
yum install fontconfig java-21-openjdk -y
yum install jenkins -y
systemctl daemon-reload
systemctl enable jenkins
systemctl start jenkins

sudo dnf install net-tools -y

## plugins

stage view
Pipeline Utility Steps

## agent - ubuntu

apt-get update
apt install openjdk-21-jre-headless
apt install nodejs
apt install docker.io
