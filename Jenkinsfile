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
        sh 'scp -o StrictHostKeyChecking=no target/*.war user@127.0.0.1:/prod/apache-tomcat-9.0.85/webapps/webapp.war'
      }
    }
  }
}
