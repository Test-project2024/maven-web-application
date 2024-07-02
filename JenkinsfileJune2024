node{
    
echo "job name is: ${env.JOB_NAME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
echo "Jenkins Home is: ${env.JENKINS_HOME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
 
 
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
     
     def mavenHome = tool name: 'maven3.9.7'
 
stage('CheckOutCode'){
git branch: 'development ', credentialsId: 'e1df468f-40d8-4ac3-b0ad-a3ea399c1e1e', url: 'https://github.com/Test-project2024/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcat'){
sshagent(['3704fccc-b40d-4b84-9efd-2a4070c57824']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.133.129.56:/opt/apache-tomcat-9.0.89/webapps"
}
}
*/

}
