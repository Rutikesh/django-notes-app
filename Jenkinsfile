@Library("SharedFiles@main") _

pipeline {
    agent {
        label 'rutikesh-agent'
    }

    stages {

        stage("From Shared Library") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Code Cloning & Checkout') {
            steps {
                script {
                    CodeClone(
                        "https://github.com/Rutikesh/django-notes-app.git",
                        "main"
                    )
                }
            }
        }

        stage('Code Building') {
            steps {
                script {
                    Build("notes-app","latest")
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                script {
                    dockerPush("notes-app", "latest")
                }
            }
        }

        stage('Code Deploying') {
            steps {
                script {
                    deploy()
                }
            }
        }
    }
}



// @Library('Shared')_
// pipeline{
//     agent { label 'dev-server'}
    
//     stages{
//         stage("Code clone"){
//             steps{
//                 sh "whoami"
//             clone("https://github.com/LondheShubham153/django-notes-app.git","main")
//             }
//         }
//         stage("Code Build"){
//             steps{
//             dockerbuild("notes-app","latest")
//             }
//         }
//         stage("Push to DockerHub"){
//             steps{
//                 dockerpush("dockerHubCreds","notes-app","latest")
//             }
//         }
//         stage("Deploy"){
//             steps{
//                 deploy()
//             }
//         }
        
//     }
// }
