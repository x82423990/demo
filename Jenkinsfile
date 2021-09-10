// /* groovylint-disable-next-line CompileStatic */
// pipeline {
//     environment {
//         imagename = 'aliyun/hacicenkins'
//         registryCredential = 'yenigul-dockerhub'
//         dockerImage = ''
//     }
//     agent {
//         docker {
//             image 'maven:3.5.4-alpine'
//             args '-v /root/.m2:/root/.m2'
//         }
//     }
//     stages {
//         stage('Cloning Git') {
//             steps {
//                 git([url: 'https://github.com/x82423990/demo.git', branch: 'master'])
//             }
//         }
//         stage('mvn build') {
//             steps {
//                 sh 'mvn -B -DskipTests clean package'
//             }
//         }
//         stage('Building image') {
//             agent {
//                 dockerfile {
//                     customWorkspace '/var/jenkins_home/workspace/demo'
//                 }
//             }
//             steps {
//                 sh 'sleep 1500'
//                 echo $projectName
//                 // script {
//                 //     dockerImage = docker.build imagename
//                 // }
//             }
//         }
//         stage('Deploy Image') {
//             steps {
//                 // script {
//                 //     /* groovylint-disable-next-line NestedBlockDepth */
//                 //     docker.withRegistry( '', registryCredential ) {
//                 //         dockerImage.push("$BUILD_NUMBER")
//                 //         dockerImage.push('latest')
//                 //     }
//                 // }
//                 echo "$BUILD_NUMBER"
//             }
//         }
//         }
//     }
pipeline {
    agent {
        docker {
            image 'maven:3.5.4-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Test') {
            agent { dockerfile true }
            steps {
                sh 'node --version'
                sh 'svn --version'
            }
        }
    }
}
