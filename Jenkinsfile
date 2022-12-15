pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MAVEN"
    }

    stages {
        
        stage ('build the project') {
           
           steps {
               // changing the working directory
                ws("/var/lib/jenkins/workspace/git-web-hook") {
                // Building the maven project
                sh 'mvn clean package'
            }
           }
            
        }
        
        stage ('Deploy to Tom cat server')
        {
            
            steps {
                
                ws("/var/lib/jenkins/workspace/git-web-hook/target") {
                    //This line is created using pipeline syntax
                   deploy adapters: [tomcat8(credentialsId: '3df1a731-66fa-4ff8-93ca-17fabe99a6ae', path: '', url: 'http://18.181.184.20:8080')], contextPath: 'maven-sample', war: '**/*.war'
                }
            }
            
        }
    }
}