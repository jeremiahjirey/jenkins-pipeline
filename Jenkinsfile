pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/jeremiahjirey/jenkins-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-jenkins-demo:latest")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f flask-demo || true'
                    sh 'docker run -d --name flask-demo -p 5000:5000 flask-jenkins-demo:latest'
                }
            }
        }
    }
}
