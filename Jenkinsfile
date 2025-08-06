pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Repo cloned automatically by Jenkins SCM'
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

    post {
        always {
            echo 'Pipeline Finished.'
        }
        failure {
            echo 'Something went wrong. Check the logs!'
        }
    }
}
