/* groovylint-disable-next-line CompileStatic */
pipeline {
    environment {
        imagename = 'aliyun/hacicenkins'
        registryCredential = 'yenigul-dockerhub'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                git([url: 'https://github.com/x82423990/demo.git', branch: 'master'])
            }
        }
        stage('mvn build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Building image') {
            steps {
                script {
                    dockerImage = docker.build imagename
                }
            }
        }
        stage('Deploy Image') {
            steps {
                // script {
                //     /* groovylint-disable-next-line NestedBlockDepth */
                //     docker.withRegistry( '', registryCredential ) {
                //         dockerImage.push("$BUILD_NUMBER")
                //         dockerImage.push('latest')
                //     }
                // }
                echo "$BUILD_NUMBER"
            }
        }
    }
}
