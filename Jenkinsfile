pipeline {
  agent { label 'test' }

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/Goviz93/python_test.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'pip3 install -r requirements.txt'
      }
    }

    stage('Lint with flake8') {
      steps {
        sh 'flake8 src/ tests/'
      }
    }

    stage('Security Scan with Bandit') {
      steps {
        sh 'bandit -r src/'
      }
    }

    stage('Run Unit Tests') {
      steps {
        sh 'pytest tests/'
      }
    }
  }

  post {
    always {
      echo 'Full test pipeline complete.'
    }
  }
}
