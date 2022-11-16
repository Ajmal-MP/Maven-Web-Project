pipeline {
    agent any
    
    tools {
        maven 'MAVEN'
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Sonar Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

    }
}
    
