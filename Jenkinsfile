pipeline{
  agent any

  stages{
    stage('Install'){
      steps{
        sh 'pip3 install -r requirements.txt --break-system-packages'
      }
    }
    stage('Test'){
      steps{
        sh 'python3 test_app.py -v'
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