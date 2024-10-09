pipeline {
    agent any

    environment {
        PATH = "$PATH"
    }

    stages {
        stage('Preparation') {
            steps {
                // Cloner le dépôt GitHub contenant le script Hello.py
                git branch: 'main', url: 'https://github.com/YanniMsr/JenkinsTest.git'
            }
        }
        stage('Build') {
            steps {
                // Exécuter le script Python
                withEnv(["PATH+EXTRA=C:/Users/ymansour/AppData/Local/Programs/Python/Python312/python.exe"]) {
                    script {
                        if (isUnix()) {
                            sh 'python Hello.py'
                        } else {
                            bat '%Python3% Hello.py'
                        }
                    }
                }
            }
        }
        stage('Archive Results') {
            steps {
                // Archiver les résultats (si besoin, adapter selon le projet)
                archiveArtifacts artifacts: '*.py', allowEmptyArchive: true
            }
        }
    }
}
