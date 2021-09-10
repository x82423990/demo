pipeline {
    environment {
        imagename = 'aliyun/hacicenkins'
        registryCredential = 'yenigul-dockerhub'
        mvnHome = '/usr/local/apache-maven-3.8.2/bin'
    }
  agent {
    node {
      label 'master'
    }
  }
    stages {
        stage('Cloning Git') {
            steps {
                git([url: 'https://github.com/x82423990/demo.git', branch: 'master'])
            }
        }
        stage('mvn build') {
            steps {
                sh '${mvnHome}/mvn -B -DskipTests clean package'
            }
        }
        stage('build image') {

            steps {
                    sh 'echo $hostname'
                    sh 'docker build -t test .'
                }
        }
        stage('Deploy Image') {
            steps {
                script{
                script{
                docker.withRegistry("https://" + registry, "ecr:eu-central-1:" + registryCredential) {
                    dockerImage.push()
                }
                }
            }
        }
    }
}