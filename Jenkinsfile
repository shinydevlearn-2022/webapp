pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
    stage ('Deploy-To-Tomcat') {
      steps {
        sshagent(['Tomcat']) {
        sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@127.0.1.1:/home/shiny/prod/apache-tomcat-9.0.85/webapps/webapp.war'
      }
      }
    }
  }
}
