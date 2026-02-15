pipeline {
    agent any
    environment {
        PYTHON_HOME = 'C:\\Users\\hug17\\AppData\\Local\\Programs\\Python\\Python313'
        PATH = "${env.PATH};${PYTHON_HOME}"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/HuggLac/jenkins_revision.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'echo "Running on Unix"'
                        sh 'python3 hello.py'
                    } else {
                        bat 'echo "Running on Windows"'
                        bat 'python hello.py'
                    }
                }
            }
        }
        stage('Affichage build') {
            steps {
                echo "Numéro du build: ${env.BUILD_NUMBER}"
                echo "Nom de la job: ${env.JOB_NAME}"
                echo "Chemin workspace: ${env.WORKSPACE}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminé.'
        }
        success {
            echo 'Le build a réussi.'
        }
        failure {
            echo 'Le build a échoué.'
        }
    }
}
