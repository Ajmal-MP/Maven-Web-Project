node {
    #to get code from git hub
    stage('git chekcout'){
        git 'https://github.com/Ajmal-MP/Maven-Web-Project' 
    }
    #compiling and package
    stage('compile package'){
        sh 'mvn package'
    }
}
