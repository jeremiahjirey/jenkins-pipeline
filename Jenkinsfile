pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                 echo 'Repo already cloned'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t flask-jenkins-demo:latest .'
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
