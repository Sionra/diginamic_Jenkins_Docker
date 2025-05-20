pipeline {
    agent any
    
    stages {
        stage('Clonage du git') {
            steps {
                git 'https://github.com/Sionra/diginamic_Jenkins_Docker.git'
            }
        }
        
        stage('Lister les fichiers et vérifie que index.html existe') {
            steps {
                bat '''
                    if exist index.html (
                      echo Le fichier index.html existe.
                    ) else (
                      echo Le fichier index.html n'existe pas.
                    )
                    '''
            }
        }
        
        stage('Lister les fichiers et vérifie que Dockerfile existe') {
            steps {
                bat '''
                    if exist Dockerfile (
                      echo Le fichier Dockerfile existe.
                    ) else (
                      echo Le fichier Dockerfile n'existe pas.
                    )
                    '''
            }
        }
    }
}