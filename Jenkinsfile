pipeline{
  agent any
  environment{
    DOCKERHUB_CREDENTIALS= credentials('dockerhub')
  }
  stages{
    stage('gitclone') {
      steps{ 
        git 'https://github.com/dodzi2022/nodeapp_test.git'
      }
    }
    stage('Build'){
      steps{ 
        sh 'Docker build -t dodzi2022/nodejsapp:1.0 .'
      }
    }
    stage('Login'){
      steps{ 
        sh 'echo $DOCKERHUB_CREDENTIALS_PWS | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push'){
      steps{ 
        sh 'docker push dodzi2022/nodejsapp:1.0 '
      }
    }
  }
  post {
    always{
      sh 'docker logout'
    }
  }
}
