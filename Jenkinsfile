pipeline {
    agent any
    
    environment {
        IMAGE_NAME = 'monsite-docker'
        CONTAINER_NAME = 'monsite-docker-conteneur'
        HOST_PORT = '8081'
        CONTAINER_PORT = '80'
    }
    
    stages {
        stage('Clonage du git') {
            steps {
                git 'https://github.com/Sionra/diginamic_Jenkins_Docker.git'
            }
        }
        
        stage('Vérifier les fichiers') {
            steps {
                script {
                    if (!fileExists('Dockerfile') || !fileExists('index.html')) {
                        error("Fichier Dockerfile ou index.html manquant.")
                    }
                }
            }
        }

        stage('Construire l’image Docker') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."
            }
        }

        stage('Supprimer conteneur existant') {
            steps {
                bat """
                docker ps -a -q -f name=%CONTAINER_NAME% > tmp.txt
                for /f %%i in (tmp.txt) do docker rm -f %%i
                del tmp.txt
                """
            }
        }

        stage('Lancer le conteneur') {
            steps {
                bat "docker run -d --name %CONTAINER_NAME% -p %HOST_PORT%:%CONTAINER_PORT% %IMAGE_NAME%"
            }
        }
    }
}