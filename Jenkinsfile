node
{
def mavenHome =tool name:"Maven 3.8.6"
stage('CheckoutCode'){
git branch: 'development', url: 'https://github.com/DevopsLearningGanesh/maven-web-application.git'
                     }

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
              }

stage('SonarReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
                    }
stage('NexusDeploy'){
sh "${mavenHome}/bin/mvn deploy"
                    }
stage('TomcatserverDeploy'){
sshagent(['d7b6dab7-6022-4a3c-9d44-e71758de1649']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.50.27:/opt/apache-tomcat-9.0.68/webapps/"
                                                   }
                           }

}
