pipeline {
    agent any

    tools {
        jdk 'jdk21'
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    sh '''
                      sonar-scanner \
                      -Dsonar.projectKey=YOUR_PROJECT_KEY \
                      -Dsonar.organization=YOUR_ORG_KEY \
                      -Dsonar.host.url=https://sonarcloud.io \
                      -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }
    }
}
