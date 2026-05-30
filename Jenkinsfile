pipeline {
  agent any

  stages {
    stage('Install') {
      steps {
        echo 'Installing dependencies...'
        sh 'pip3 install -r requirements.txt --break-system-packages'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'python3 -m pytest test_calculator.py --junitxml=results.xml -v'
      }
    }
  }

  post {
    always {
      junit 'results.xml'
      echo 'Test report published!'
    }
    success { echo 'All tests passed!' }
    failure { echo 'Some tests failed — check the report.' }
  }
}
