pipeline {
    agent any

    stages{
        stage("clone code"){
            steps {
                echo "code cloning hogya repo se"
                git url: "https://github.com/iam-mohanty/docker-compose-jenkins-declarative-nodeapp.git", branch: "master"
            }
        }
        stage("code build"){
            steps {
                echo "code build v karliye"
                sh "docker build . -t my-node-app:latest"
            }
        }
        stage("code test"){
            steps {
                echo "code testing hogya"
            }
        }
        stage("Push to Docker Hub"){
            steps {
                echo "pushing the image to docker hub"
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker tag my-node-app ${env.dockerHubUser}/my-node-app:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/my-node-app:latest"
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
