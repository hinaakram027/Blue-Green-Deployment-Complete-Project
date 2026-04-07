<img width="1365" height="673" alt="jenkins blue green deployment" src="https://github.com/user-attachments/assets/bfc5e3f3-d48b-43d5-9634-aee7dd86f0c2" />

## Step 1: Create EC2 Instance
 IAM user with **access keys and secret access keys**
## Step 2: Install ```AWS CLI```, ```Kubectl```, ```EKSCTL```:
 ```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

apt install unzip

unzip awscliv2.zip
```
- ```Kubectl``` - kubectl is the command-line tool used to interact with Kubernetes clusters.
```
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.30.2/2024-07-12/bin/linux/amd64/kubectl

chmod +x kubectl

mv kubectl /usr/local/bin/kubectl
```    
- ```EKSCTL``` - eksctl is a command-line tool for managing Amazon EKS (Elastic Kubernetes Service) clusters.
```
curl -LO "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz"

tar -xzf eksctl_Linux_amd64.tar.gz

sudo mv eksctl /usr/local/bin/

eksctl version
```
## Step 3: AWS Configure - 
        ○ Access Key - Your_Access_Key
        ○ Access Secret Key - Your Access_secret_key
## Step 4: Create EKS Cluster
```
eksctl create cluster --name java-complete-project --region us-west-1 --node-type t3.micro --nodes-min 1 --nodes-max 2
```
<img width="1365" height="676" alt="eks cluster" src="https://github.com/user-attachments/assets/7edadd9d-9c7e-4ea9-9e1c-c6662af5113e" />

## Step 5: Configure EKS Cluster
```
eksctl  create cluster --name java-complete-project --region us-west-1
```

```
aws eks update-kubeconfig --name java-complete-project --region us-west-1
```
## Step 6: Docker Installation 

```
sudo apt install docker.io -y
```

## Step 7: Give Permission Docker 

```
sudo usermod -aG docker $USER
sudo chmod 777 /var/run/docker.sock
```
## Step 8: SonarQube Installation 

```
docker run -itd --name sonarqube-server -p 9000:9000 sonarqube:lts-community
```
<img width="1365" height="677" alt="Sonar Qube Report" src="https://github.com/user-attachments/assets/45b8da81-e1ac-47bb-9d56-56c74d48d939" />

## Step 9: Trivy Installation 

```
sudo apt-get install wget gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```
## Step 10: Jenkins Installation

```
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```

```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```
<img width="1365" height="383" alt="jenkins kubernetes secret" src="https://github.com/user-attachments/assets/3493ff5b-f33c-46c9-8aab-7e865ac2ba96" />
<img width="1365" height="679" alt="groovy syntax" src="https://github.com/user-attachments/assets/1aff8359-0278-4b0c-9e40-4c411ebcb202" />
<img width="1362" height="674" alt="jenkins pipeline half 1 pic" src="https://github.com/user-attachments/assets/e7770125-ca78-4ddf-8f9d-06c015b374a3" />
<img width="1365" height="676" alt="jenkins pipeline half 2 pic" src="https://github.com/user-attachments/assets/29c9caae-9ab7-4ef5-8c0d-d26f0d8de459" />
<img width="1365" height="679" alt="load balancer" src="https://github.com/user-attachments/assets/0dbef395-16fe-4d48-9f1a-c9dbf7046098" />









        
