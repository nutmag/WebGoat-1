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
    
    stage ('SAST') {
      steps {
        withSonarQubeEnv('sonar') {
          sh 'mvn clean package'
          sh 'mvn sonar:sonar \
              mvn sonar:sonar \
              -Dsonar.projectKey=Webtest \
              -Dsonar.host.url=http://vast.fruxlabs.com:9000 \
              -Dsonar.login=1c32eb755fcb090d8501dab577db02912d13abd4'
        }
      }
    }
    
    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
  }
}
