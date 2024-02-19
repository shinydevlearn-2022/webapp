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
        sh 'target/*.war ubuntu@127.0.0.1:/home/shiny/prod/apache-tomcat-9.0.85/webapps/webapp.war'
      }
    }
  }
}
