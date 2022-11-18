
# Jenkins CI-CD For Auto Deploy Maven Project In Tomcat Server

This is a simple CI-CD pipeline of Jenkins to auto deploy maven build to tomcat server

## Screenshots

![App Screenshot](https://i.postimg.cc/PJkrMT5m/jenkins-maven-tomcat.png)

## git clone link


```bash
  git clone https://github.com/Ajmal-MP/Maven-Web-Project.git
```

## Requirements

- Ubuntu instance

- Jenkins setup

    [Link to jenkins setup](https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-20-04)

- Maven setup

    [Link to Maven setup](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

- Tomcat setup
   
    [Link to Tomcat setup](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-10-on-ubuntu-20-04)

## Jenkins pipeline for auto deploy

```javascript
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
```



  
    




