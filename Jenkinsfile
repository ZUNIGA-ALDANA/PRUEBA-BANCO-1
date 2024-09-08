//@Library ('main-lib') _
//#mainPipe()
pipeline {
    agent any

    stages {
        stage('Get GitHub Actions results') {
            steps {
                script {
                    // Comando curl para obtener el archivo de GitHub Actions
                    sh 'curl -u $GITHUB_TOKEN: -O https://api.github.com/repos/OWNER/REPO/actions/artifacts/ARTIFACT_ID.zip'
                    // Descomprimir y mostrar los resultados en consola
                    sh 'unzip ARTIFACT_ID.zip'
                    sh 'cat dependency-review-report.json'
                }
            }
        }
    }
}
