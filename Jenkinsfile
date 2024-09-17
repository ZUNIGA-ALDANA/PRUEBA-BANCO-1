pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Prueba de Stage1'
            }
        }
        stage('Build') {
            steps {
                echo 'Prueba de Stage2'
            }
        }
        stage('Test') {
            steps {
                echo 'Prueba de Stage3'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Prueba de Stage4'
            }
        }
        stage('Check Dependabot Alerts') {
            steps {
                script {
                    def response = sh(script: """
                    curl -H "Accept: application/vnd.github+json" \
                    -H "Authorization: token Iv23liydBQidT7PkTxyW" \
                    https://api.github.com/repos/ZUNIGA-ALDANA/PRUEBA-BANCO-1/dependabot/alerts
                    """, returnStdout: true).trim()
                    
                    echo "Dependabot Alerts: ${response}"
                }
            }
        }
        
    }
}

        