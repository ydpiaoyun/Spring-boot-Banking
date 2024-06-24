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
         sh 'docker build -t registry.cn-hangzhou.aliyuncs.com/piaoyun/demo:${tag} .'
      }
    }
    stage('push docker image'){
      environment {
        ALIYUN_CREDS = credentials('aliyun-image')
      }
      steps {
        sh '''docker login --username=$ALIYUN_CREDS_USR --password=$ALIYUN_CREDS_PSW registry.cn-hangzhou.aliyuncs.com
        docker push registry.cn-hangzhou.aliyuncs.com/piaoyun/demo:${tag}
        docker rmi registry.cn-hangzhou.aliyuncs.com/piaoyun/demo:${tag}'''
      }
    }
  }
}
