pipeline {
    agent {
        label 'rutikesh-agent'
    }

    stages {

        stage('Code Cloning') {
            steps {
                echo 'This is for code cloning'
                // git url: 'https://github.com/Rutikesh/django-notes-app.git', branch: 'main'
                echo 'Code cloning successful'
            }
        }

        stage('Code Building') {
            steps {
                echo 'This is for code building'
                sh 'whoami'
                sh 'docker build -t notes-app:latest .'
            }
        }

        stage('Code Testing') {
            steps {
                echo 'This is for code testing'
                // Add real tests later
            }
        }

        stage('Code Push in Docker Hub') {
            steps {
                echo 'Pushing image to Docker Hub'

                withCredentials([
                    usernamePassword(
                        credentialsId: 'DoDjJe',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {
                    sh '''
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                        docker tag notes-app:latest $DOCKER_USER/notes-app:latest
                        docker push $DOCKER_USER/notes-app:latest
                    '''
                }
            }
        }

        stage('Code Deploying') {
            steps {
                echo 'Deploying application using Docker Compose'
                sh 'docker compose up -d'
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
