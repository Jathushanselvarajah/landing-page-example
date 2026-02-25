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
                echo 'Fichiers récupérés :'
                sh 'ls -la'
            }
        }
        stage('Deploy to Azure') {
            steps {
                sh '''
                    ssh -o StrictHostKeyChecking=no -i /var/jenkins_home/.ssh/id_ed25519 azureuser@51.120.126.140 << 'EOF'
                    cd ~/landing-page-example
                    git pull origin main
                    docker build -t landing-page .
                    docker stop landing || true
                    docker rm landing || true
                    docker run -d --name landing -p 80:80 landing-page
                    echo "Déploiement terminé !"
EOF
                '''
            }
        }
    }
}
