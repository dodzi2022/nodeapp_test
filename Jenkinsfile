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
        sh 'docker build -t dodzi2022/nodejsapp:1.0 .'
      }
    }
    stage('Login'){
      steps{ 
        #sh 'echo $DOCKERHUB_CREDENTIALS_PWS | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        sh 'docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PWS'
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
