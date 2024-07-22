node('built-in') {
    stage('ContinuousDownload') {
    git 'https://github.com/P2PConcept/maven.git'
    }
    stage('ContinuousBuild') {
    sh 'mvn package'
    }
    stage('ContinuousDeploy') {
    sh 'scp /var/lib/jenkins/workspace/Scripted-Pipeline/webapp/target/webapp.war ubuntu@172.31.18.11:/var/lib/tomcat10/webapps/testapp.war'
    }
    stage('ContinuousTesting') {
    git 'https://github.com/P2PConcept/testingcode.git'
    sh 'java -jar /var/lib/jenkins/workspace/Scripted-Pipeline/testing.jar'
    }
    stage('ContinuousDelivery') {
    sh 'scp /var/lib/jenkins/workspace/Scripted-Pipeline/webapp/target/webapp.war ubuntu@172.31.18.48:/var/lib/tomcat10/webapps/prodapp.war'
    }
}
