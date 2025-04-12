node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build Docker image') {
        app = docker.build("anunyan1/jenkins-demo")
    }
    stage('Push to Docker Hub') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
        }
    }
}