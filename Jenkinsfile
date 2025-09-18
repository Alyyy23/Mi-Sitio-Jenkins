pipeline {
    agent any

    stages {
        stage('1. Clonar Código') {
            steps {
                echo 'Obteniendo el código más reciente desde GitHub...'
                git url: 'https://github.com/Alyyy23/Mi-Sitio-Jenkins.git', branch: 'main'
            }
        }

        stage('2. Desplegar en Nginx') {
            steps {
                echo 'Copiando archivos al servidor Nginx...'

                // Listar archivos antes de copiar para depuración
                sh 'echo "Archivos en workspace:" && ls -l'

                // Copiar archivos al directorio de Nginx
                // sudo necesario si Jenkins no tiene permisos directos
                sh 'sudo cp -f *.html /usr/share/nginx/html/'

                // Verificar que se copiaron
                sh 'echo "Archivos en Nginx:" && ls -l /usr/share/nginx/html/'
            }
        }
    }

    post {
        success {
            echo 'Despliegue completado. Accede a http://localhost para verificar.'
        }
        failure {
            echo 'Ocurrió un error durante el despliegue.'
        }
    }
}
