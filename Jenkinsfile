node {
    stage('git chekcout'){
        git branch: 'main', url: 'https://github.com/Ajmal-MP/Maven-Web-Project'
    }
    stage('compile package'){
        sh 'mvn package'
    }
}
