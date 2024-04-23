pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("simple-python-calculator:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image("simple-python-calculator:${env.BUILD_NUMBER}").inside {
                        sh 'python calculator.py --test'
                    }
                }
            }
        }
    }
}
