pipeline {
    agent any
    parameters {
        string(name: 'FRONTEND_VERSION', defaultValue: 'latest')
    }
    stages {
        stage ('Update Image Tags') {
            steps {
                script {
                    withDockerRegistry([ credentialsId: "dockerhub-repo", url: "" ]) {
                        def frontendImage = docker.image("hsndocker/frontend:${params.FRONTEND_VERSION}")
                        frontendImage.push("latest")

                        def nginxImage = docker.image("hsndocker/nginx:${params.FRONTEND_VERSION}")
                        nginxImage.push("latest")
                    }
                }
                
            }
        }
    }
}