pipeline {

    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/yashi-design/flask-cicd-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Debug') {
    steps {
        sh 'pwd'
        sh 'ls -la'
        sh 'which docker'
        sh 'docker --version'
           }
       }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f flask-app || true

                docker run -d \
                --name flask-app \
                -p 5000:5000 \
                flask-app
                '''
             }
           }
       }
    }
  }
}
