//@Library ('main-lib') _
//#mainPipe()

pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'my-github-credentials'
            }
        }
        stage('Analyze Dependabot Alerts') {
            steps {
                script {
                    def alerts = sh(script: 'curl -s https://api.github.com/repos/owner/repo/security/advisories', returnStdout: true).trim()
                    def jsonAlerts = new JsonSlurper().parseText(alerts)

                    // Iterar sobre las alertas y clasificarlas
                    jsonAlerts.advisories.each { advisory ->
                        println "Vulnerabilidad: ${advisory.description}"
                        println "Gravedad: ${advisory.severity}"

                        // Lógica para clasificar las vulnerabilidades
                        if (advisory.severity == 'CRITICAL') {
                            // Acción para vulnerabilidades críticas (por ejemplo, enviar notificación)
                            echo 'Vulnerabilidad crítica detectada!'
                        } else if (advisory.severity == 'HIGH') {
                            // Acción para vulnerabilidades altas
                        } else {
                            // Acción para vulnerabilidades medias o bajas
                        }
                    }
                }
            }
        }
    }
}