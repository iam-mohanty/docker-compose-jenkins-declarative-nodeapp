# docker-compose-jenkins-declarative-nodeapp🚀⛴️👇

# jenkins-nodeapp👇😎

# 1. install ubuntu 

create aws ubuntu-22 server , login as : ubuntu 

sudo apt-get update 

sudo apt install docker.io -y 

sudo usermod -aG docker $USER

sudo reboot , again login

# 2. jenkins install

sudo apt install openjdk-17-jre -y

java --version

go to jenkins.io -> copy & paste binary , key files
  
sudo apt-get update

sudo apt-get install jenkins

login jenkins

# 3. start project

create pipeline project

mention anything inside description

github projects : mention ur github repo ; https://github.com/iam-mohanty/docker-compose-jenkins-declarative-nodeapp.git

add syntax in pipeline section (paste it from jenkinsfile) , build

sudo usermod -aG docker jenkins

sudo reboot

again build now

# 4. create docker-hub credential

manage jenkins -> credentials -> goto system -> global credential -> add credential -> mention ur dockerhub username & pw , id : dockerHub

# 5. install docker-compose

sudo apt-get install docker-compose -y

# 6. access app

public-ip:8000
