pipeline {
    agent any

    environment {
        SONARQUBE = 'MySonar'
    }

    tools {
        maven 'maven 3.8.1'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ganeshhhhhh/demo-app.git'                 }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE}") {
                    sh 'mvn sonar:sonar -Dsonar.projectKey=demo-app -Dsonar.host.url=http://3.110.118.240:9000'
                }
            }
        }
    }
}

