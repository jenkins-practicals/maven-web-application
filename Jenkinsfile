pipeline {
	/* insert Declarative Pipeline here */

agent any
	
/*
agent {
label '<label-name>'

} 
*/

options {
  timestamps
  buildDiscarder logRotator(artifactDaysToKeepStr: '2', artifactNumToKeepStr: '2', daysToKeepStr: '2', numToKeepStr: '2')
}

tools {
  maven 'my-maven'  // or maven "maven3.9.3" ,similarly git ant 
} //tools

// to add the triaggers before the stages  pollscm('* * * * *'), corn  all are functions
/* we write multiple stage in stages only */

stages{

stage('checkout') {
  steps {
    git branch: 'development', url: 'https://github.com/jenkins-practicals/maven-web-application.git'
  }
} //checkout stage

stage('build'){
  steps{
  sh 'mvn clean package'
  }
} //build stage

stage('Execute sonarqube report'){
  steps{
  sh "mvn sonar:sonar"
  }
  /* sonfigure this sonarqube server details in the pom.xml file*/
} //Execute sonarqube report stage

/*
stage('upload artifact to nexus'){
  steps{
  sh "mvn deploy"
  }
} //upload artifact to nexus stage
*/

} //stages
} //pipeline

