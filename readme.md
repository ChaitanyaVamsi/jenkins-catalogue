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

## Reset the failed systemd state and retry

sudo systemctl reset-failed jenkins
sudo systemctl start jenkins
systemctl status jenkins

## plugins

stage view
Pipeline Utility Steps - to read packagejson
sonarqube scanner
Aws steps
ansicolor

## agent - ubuntu

dnf install nodejs -y --- for reddhat

apt-get update
sudo apt update
sudo apt install -y git
apt install npm
apt install openjdk-21-jre-headless
apt install nodejs
apt install docker.io

## ecr on slave

---

## if there is no aws cli on slave you get erro slave should have aws cli

sudo apt update
sudo apt install -y unzip curl
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version

## if image does not get pushed" permission denied" error

sudo usermod -aG docker ubuntu
sudo systemctl restart docker

## sonarqube docker

docker run -d --name sonarqube \
 -p 9000:9000 \
 -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true \
 sonarqube:community

# docker

yum install -y yum-utils
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
systemctl start docker
systemctl enable docker
usermod -aG docker ec2-user

## ubuntu jenkins

apt update

sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
 https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
 https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
 /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins

apt install npm
apt install docker.io
sudo usermod -aG docker ubuntu
sudo systemctl restart docker

#terraform
yum install -y yum-utils
yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
yum -y install terraform

#trivy
curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sudo sh -s -- -b /usr/local/bin v0.68.2

#aws cli
sudo apt update
sudo apt install -y unzip curl
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
