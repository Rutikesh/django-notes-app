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
                    Build("notes-app","latest","rutikesh1907")
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
