pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/sijihendrix/monolith-to-microservices-project.git', branch: 'deployment')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker push anileloye/frontend:latest'
        sh 'docker push anileloye/api-user:latest'
        sh 'docker push anileloye/api-feed:latest'
        sh 'docker push anileloye/reverseproxy:latest'
      }
    }


    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'anileloye'
        DOCKERHUB_PASSWORD = 'Oluwasijibomi17_'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push anileloye/frontend:latest'
        sh 'docker push anileloye/api-user:latest'
        sh 'docker push anileloye/api-feed:latest'
        sh 'docker push anileloye/reverseproxy:latest'
      }
    }

  }
}


