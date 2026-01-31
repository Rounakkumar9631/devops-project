pipeline {
  agent any

  stages {

    stage('Clone Repo') {
      steps {
        git 'https://github.com/Rounakkumar9631/devops-project.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t devops-app:latest .'
      }
    }

    stage('Push Image') {
      steps {
	sh 'docker login -u rounakj06 -p rounakjaiswal'
	sh 'docker tag myapp:latest rounakj06/devops-app:latest'
	sh 'docker push rounakj06/devops-app:latest'
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f deployment.yaml'
        sh 'kubectl apply -f service.yaml'
      }
    }
  }
}