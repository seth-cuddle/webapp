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
                sh 'scp -o StrictHostKeyChecking=no **/*.war ubuntu@ec2-3-80-188-95.compute-1.amazonaws.com:/prod/apache-tomcat-9.0.93/webapps/webapp.war'
             
              }      
           }       
    }
    
    //fin stages
  }

  
}
