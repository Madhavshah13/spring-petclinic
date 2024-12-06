pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git credentialsId: 'github-credentials', branch: 'main', url: 'https://github.com/Madhavshah13/spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Static Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh './mvnw sonar:sonar'
                }
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }
    }
}

