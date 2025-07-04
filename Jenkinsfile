pipeline {
    agent any

    environment {
        SONARQUBE = 'MySonar'  // This must match Jenkins > SonarQube server config
    }

    tools {
        maven 'maven'  // ✅ Use the correct name as per Jenkins configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ganeshhhhhh/demo-app.git', branch: 'main'
            }
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
