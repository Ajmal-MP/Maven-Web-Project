node {
    tools {
     maven 'MAVEN'
    }
    stage('build'){
        steps {
          sh 'maven clean package'
        }
    }
    stage('Sonar Analysis'){
        steps {
            withSonarQubeEnv('SonarQube') {
             sh 'mvn sonar:sonar'
            }
        }
    }
    
    stage("Quality Gate") {
        steps {
            timeout(time:1, unit: 'HOURS') {
                waitForQualityGate abortPipeline:true
            }
        }
    }
}
