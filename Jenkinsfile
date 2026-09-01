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
                sh 'npm install'
            }
        }
        stage("Build"){
            steps{
                sh 'npm run build'
            }
        }
        stage("Test"){
            steps{
                sh 'npm test'
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