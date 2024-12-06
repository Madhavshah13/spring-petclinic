pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                sh '''
                    chmod +x mvnw
                    ./mvnw clean package
                '''
            }
        }
        stage('Execute') {
            steps {
                sh '''
                    cd target
                    java -jar spring-petclinic-3.3.0-SNAPSHOT.jar --server.port=8085 > petclinic.log 2>&1 &
                    sleep 300
                '''
            }
        }
    }
}

