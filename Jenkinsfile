pipeline {
    agent any

    environment {
        GITHUB_TOKEN = credentials('DENISSE_TOKEN') // Asegúrate de haber agregado el token en Jenkins
    }

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

        stage('Fetch Dependabot Alerts') {
            steps {
                script {
                    def vulnerabilities = dependabotScan() // Asumiendo que dependabotScan() es una función proporcionada por el plugin
                    if (vulnerabilities.size() > 0) {
                        echo "Se han encontrado las siguientes vulnerabilidades:"
                        vulnerabilities.each { vulnerability ->
                            echo "- ${vulnerability.dependency}: ${vulnerability.severity} - ${vulnerability.title}"
                        }
                        error "Se han encontrado vulnerabilidades críticas. Deteniendo el pipeline."
                    } else {
                        echo "No se han encontrado vulnerabilidades."
                    }
                }
            }
        }
    }
}
