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
                echo 'Prueba de Alerta Dependabots'
                script {
                    // URL de la API de GitHub para obtener las alertas de seguridad
                    def apiUrl = 'https://api.github.com/repos/ZUNIGA-ALDANA/PRUEBA-BANCO-1/dependabot/alerts'

                    // Realizar la solicitud a la API
                    def response = sh(
                        script: """
                            curl -s -H "Authorization: token $GITHUB_TOKEN" \
                            -H "Accept: application/vnd.github+json" \
                            $apiUrl
                        """,
                        returnStdout: true
                    ).trim()

                    // Procesar la respuesta (puede ser un JSON con las alertas)
                    if (response) {
                        def json = readJSON text: response
                        echo "Found ${json.size()} Dependabot Alerts"

                        // Iterar sobre las alertas y mostrarlas en la salida
                        json.each { alert ->
                            echo "Package: ${alert.security_advisory.identifier} - Severity: ${alert.security_advisory.severity}"
                            echo "Description: ${alert.security_advisory.description}"
                            echo "More info: ${alert.html_url}"
                        }
                    } else {
                        echo "No Dependabot Alerts found."
                    }
                }
            }
        }
    }
}

