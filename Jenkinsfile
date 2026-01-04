@Library("SharedFiles") _
pipeline {
    agent {
        label 'rutikesh-agent'
    }

    stages {

        stage("from shared library"){
            steps{
                script{
                    hello()
                }
            }
        }
        // stage('Check Branch') {
        //     steps {
        //         script {
        //             // For Generic Webhook / normal pipeline
        //             def branchName = sh(
        //                 script: "git rev-parse --abbrev-ref HEAD || echo main",
        //                 returnStdout: true
        //             ).trim()

        //             if (branchName != 'main') {
        //                 error "Not main branch. Skipping pipeline."
        //             }

        //             echo "Running on main branch"
        //         }
        //     }
        // }

        stage('Code Cloning') {
            steps {
                echo 'Cloning source code'
                checkout scm
                echo 'Code cloning successful'
            }
        }

        // stage('Code Building') {
        //     steps {
        //         echo 'Building Docker image'
        //         sh 'whoami'
        //         sh 'docker build -t notes-app:latest .'
        //     }
        // }

        // stage('Code Testing') {
        //     steps {
        //         echo 'Running tests (placeholder)'
        //     }
        // }

        // stage('Push Image to Docker Hub') {
        //     steps {
        //         echo 'Pushing image to Docker Hub'
        //         withCredentials([
        //             usernamePassword(
        //                 credentialsId: 'DoDjJe',
        //                 usernameVariable: 'DOCKER_USER',
        //                 passwordVariable: 'DOCKER_PASS'
        //             )
        //         ]) {
        //             sh '''
        //                 set -e
        //                 echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
        //                 docker tag notes-app:latest $DOCKER_USER/notes-app:latest
        //                 docker push $DOCKER_USER/notes-app:latest
        //             '''
        //         }
        //     }
        // }

        // stage('Code Deploying') {
        //     steps {
        //         echo 'Deploying application using Docker Compose'
        //         sh 'docker compose up -d'
        //     }
        // }
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
