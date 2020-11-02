pipeline {

agent any

tools {
    maven 'maven'
}

stages {
    
    stage ("Checkout") {
        steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Ask-Sanjeev/DevOps-Demo-WebApp.git']]])
            }
        }

    stage ("Build") {
    
      steps {
          sh 'mvn clean install -f 'DevOps-Demo-WebApp/pom.xml'
          }
        }
        
    stage ("Deploy") {
    
      steps { 
          deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://34.69.207.41:8080/')], contextPath: '/QAWebapp', war: '**/*.war'
          }
      }
      
      stage ("Slack notification") {
          steps {
              slackSend (channel: 'alerts', message: "deployment is successful, here is the info - Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
          }
      }
 }
 }
