node{
        stage('Clone Repo') {
            git credentialsId: 'e348001a-f702-4cc1-974c-4688f4e8c976', url: 'https://github.com/ashokitschool/maven-web-app.git'
        }
        
        stage ('Maven Clean Build'){
            def mavenHome = tool name: "Maven-3.8.6", type: "maven"
            def mavenCMD = "${mavenHome}/bin/mvn"
            sh "${mavenCMD} clean package"
        }
        stage ('Code Quality Check'){
			withSonarQubeEnv('Sonar-Server-7.8'){
			    def mavenHome = tool name: "Maven-3.8.6", type: "maven"
			    def mavenCMD = "${mavenHome}/bin/mvn"
			    sh "${mavenCMD} sonar:sonar"
			}
        }
        stage ('Nexus Build'){ 
            nexusArtifactUploader artifacts: [[artifactId: '01-maven-web-app', classifier: '', file: 'target/01-maven-web-app', type: 'war']], credentialsId: 'Nexus-Cred', groupId: 'com.avinash', nexusUrl: '3.132.212.118:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'avinash-snapshot', version: '1.0-SNAPSHOT'
        }
        stage ('Deploy'){
            sshagent(['Tomcat-Server-Agent']) {
		    sh 'scp -o StrictHostKeyChecking=no target/01-maven-web-app.war ec2-user@13.235.75.254:/home/ec2-user/apache-tomcat-9.0.64/webapps'
            }      
}
