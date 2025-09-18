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
                echo 'Copiando archivos al volumen de Nginx...'

                // Listar archivos antes de copiar
                sh 'echo "Archivos en workspace:" && ls -l'

                // Copiar archivos HTML al volumen compartido
                sh 'cp -f *.html /var/jenkins_home/nginx-html/'

                // Verificar que se copiaron
                sh 'echo "Archivos en volumen de Nginx:" && ls -l /var/jenkins_home/nginx-html/'
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
