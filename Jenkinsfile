pipeline {
    agent any
    
    tools {
     maven 'MAVEN'
    }
    stages('build'){
        steps {
          sh 'maven clean package'
        }
    }
    stages('Sonar Analysis'){
        steps {
            withSonarQubeEnv('SonarQube') {
             sh 'mvn sonar:sonar'
            }
        }
    }
    
    stages("Quality Gate") {
        steps {
            timeout(time:1, unit: 'HOURS') {
                waitForQualityGate abortPipeline:true
            }
        }
    }
}
