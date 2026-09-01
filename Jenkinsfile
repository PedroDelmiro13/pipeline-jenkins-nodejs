pipeline{
    agent any
    
    stages {
        stage("Checkout"){
            steps{
                git branch: "main",
                url: "https://github.com/carlhenriquex/pipeline-jenkins-nodejs.git"
            }
        }
        stage("Install"){
            steps{
                bat 'npm install'
            }
        }
        stage("Build"){
            steps{
                bat 'npm run build'
            }
        }
        stage("Test"){
            steps{
                bat 'npm test'
            }
        }
    }
    post {
        success {
            echo "Sucesso"
        }
        failure {
            echo "Fracasso"
        }
    }
}