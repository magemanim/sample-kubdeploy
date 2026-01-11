pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Copy Files') {
      steps {
        sh '''
          sudo mkdir -p /var/lib/jenkins/webapp
          sudo cp app/index.html /var/lib/jenkins/webapp/index.html
        '''
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f k8s/deployment.yaml'
      }
    }
  }
}

