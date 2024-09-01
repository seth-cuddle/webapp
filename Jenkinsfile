pipeline{
agent any
tools{
  maven 'maven'
}
  stages{
    stage ('Initialized'){
      steps{
        sh '''
              echo "PATH =${PATH}"
              echo "M2_HOME = ${M2_HOME}"
        '''
      }
    }
    stage('Build'){
      steps{
      sh 'mvn clean package'
      }
    }
    stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/WebApp.war ubuntu@3.80.188.95:/prod/apache-tomcat-9.0.93/webapps/webapp.war'
             
              }      
           }       
    }
    
    //fin stages
  }

  
}
