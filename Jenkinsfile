pipeline {
  agent { docker { image 'python:3.8' } }
  stages {
    stage('build') {
      steps {
			sh 'python -m venv .venv'
			sh '''
				. .venv/bin/activate
    				pip install --upgrade pip
				pip install -r requirements.txt
			
			'''
      
      }
    }
    stage('test') {
      steps {
			sh '''
				. .venv/bin/activate
				pytest  application_test.py
				
			'''
       
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}
