pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/tu_usuario/tu_repositorio.git'
                echo 'Código clonado exitosamente!'
            }
        }
    }
}