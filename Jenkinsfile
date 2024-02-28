pipeline {
    agent any
            stages {
            stage('Git clone') {
            steps {
               git credentialsId: '6ea14d1d-33b7-470d-b68d-25e3964184fb', url: 'https://github.com/ashokitschool/maven-web-app.git'
            }
        }
   }
}
