pipeline {
  agent any
  environment {
    PYTHON_PATH = 'C:/Users/SRIJA/AppData/Local/Programs/Python/Python313;C:/Users/SRIJA/AppData/Local/Programs/Python/Python313/Scripts'
    SONAR_TOKEN = credentials('sonarqube_id')  // Jenkins credentials for SonarQube token
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        bat '''
        set PATH=%PYTHON_PATH%;%PATH%
        pip install -r requirements.txt
        '''
      }
    }
    stage('SonarAnalysis') {
      steps {
        bat '''
        set PATH=%PYTHON_PATH%;%PATH%
        sonar-scanner.bat -Dsonar.projectKey=p2 ^
        -Dsonar.sources=. ^
        -Dsonar.host.url=http://localhost:9000 ^
        -Dsonar.token=%SONAR_TOKEN%
        '''
      }
    }
  }
  post {
    success {
      echo 'Build and analysis went well.'
    }
    failure {
      echo 'Build or analysis failed.'
    }
  }
}
