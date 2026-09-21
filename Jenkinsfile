pipeline{
    agent any
 
    stages {
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
 
        stage("SAST - Semgrep"){
            steps{
                bat 'pip install semgrep'
                bat 'semgrep scan --config p/security-audit --config p/owasp-top-ten --error'
            }
        }

        stage("Start app"){
            steps{
                bat 'start /B npm start'
                bat 'timeout /T 10'
            }
        }
 
        stage("DAST - OWASP ZAP"){
            steps{
                bat 'docker run --rm -t owasp/zap2docker-stable zap-baseline.py -t http://host.docker.internal:3000 -I'
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
 