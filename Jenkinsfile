pipeline {
  agent any

  stages{
    stage('checkout from git'){
      steps {
        checkout scmGit(branches: [[name: '${tag}']], extensions: [], userRemoteConfigs: [[url: 'git@github.com:ydpiaoyun/Spring-boot-Banking.git']])
      }
    }
    stage('build from maven'){
      steps {
        sh 'mvn package -Dmaven.test.skip=true'
      }
    }
    stage('build docker image'){
      steps {
         
      }
    }
    stage('push docker image'){
      steps {
      }
    }
  }
}
