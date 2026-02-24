pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Jathushanselvarajah/landing-page-example.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Vérification des fichiers...'
                sh 'ls -la'
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp -o StrictHostKeyChecking=no -i /var/jenkins_home/.ssh/id_ed25519 index.html jathus92@ssh-jathus92.alwaysdata.net:www/'
            }
        }
    }
}
