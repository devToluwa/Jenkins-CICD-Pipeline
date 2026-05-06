pipeline{
  agent any

  stages{
    stage('Install'){
      steps{
        sh 'pip install -r requirements.txt'
      }
    }
    stage('Test'){
      steps{
        sh 'pytest test_app.py -v'
      }
    }
    stage('Docker Build'){
      steps{
        sh 'docker build -t flask-jenkins-app .'
      }
    }
  }

  post{
    success{
      echo 'Pipeline Passed :)'
    }
    failure{
      echo 'Pipeline Failed :('
    }
  }

}