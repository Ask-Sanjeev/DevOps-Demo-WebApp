pipeline {

agent any

stages {

    stage ("build") {
    
      steps {
          echo 'building the application...'
          }
        }
        
    stage ("deploy") {
    
      steps { 
          deploy adapters: [tomcat9(crdentialsId: '', path: '', url: 'http://34.69.207.41:8080/')],contextPath:null, war: '**/*.war'
          }
      }
 }
 }
