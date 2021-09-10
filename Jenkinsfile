// /* groovylint-disable-next-line CompileStatic */
pipeline {
    environment {
        imagename = 'aliyun/hacicenkins'
        registryCredential = 'yenigul-dockerhub'
        dockerImage = ''
    }
    agent {label 'master'}
    stages {
        stage('Cloning Git') {
            agent any
            steps {
                git([url: 'https://github.com/x82423990/demo.git', branch: 'master'])
            }
        }
        stage('mvn build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('build image') {
            agent {
                sh 'docker build -t test .'
            }
            steps {
                    sh 'echo $hostname'
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
// pipeline {
//     agent none
//     // {
//     //     docker {
//     //         image 'maven:3.5.4-alpine'
//     //         args '-v /root/.m2:/root/.m2'
//     //     }
//     // }
//     stages {
//         stage('echo') {
//             agent none
//             steps {
//                 echo env.NODE_NAME
//             }
//         }
//         stage('Test') {
//             agent { dockerfile true }
//             steps {
//                 sh 'node --version'
//                 sh 'svn --version'
//             }
//         }
//     }
// }
