pipeline {
    agent any

    stages {
        stage('code clone') {
            steps {
                echo "code cloning hogya repo se"
                git url: "https://github.com/urdevops/jenkins-nodejs-project.git", branch: "master"
            }
        }
        stage('code build') {
            steps {
                echo "code build v karliye"
                sh "docker build . -t mynodeappimg:latest"
            }
        }
        stage('code test') {
            steps {
                echo "code testing hogya"
            }
        }
        stage('push to docker hub') {
            steps {
                echo "pushing the image to docker hub"
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker tag mynodeappimg ${env.dockerHubUser}/mynodeappimg:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/mynodeappimg:latest"
                }
            }
        }
        stage('deploy') {
            steps {
                echo "deploying the container"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
