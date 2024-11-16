pipeline {
    agent any

    tools {
        nodejs 'NodeJS_Latest' // Jenkins'te Global Tool Configuration'da tanımladığınız Node.js'i kullanacak
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Projeyi GitHub'dan alıyoruz
                git branch: 'main', url: 'https://github.com/muzafferkoluman/wildrydes-site.git'
            }
        }

        stage('Debug PATH') {
            steps {
                sh '''
                echo "Current PATH: $PATH"
                node -v
                npm -v
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                // PATH'i manuel olarak ekliyoruz ve npm komutunu çalıştırıyoruz
                sh '''
                export PATH=$PATH:/usr/local/bin
                echo "Updated PATH: $PATH"
                node -v
                npm -v
                npm install
                '''
            }
        }

        stage('Run Tests') {
            steps {
                // Test komutlarını çalıştırıyoruz
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                // Projeyi build ediyoruz
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Eğer dağıtım işlemi gerekiyorsa bu aşamada yapabilirsiniz
                echo 'Deployment step (deploy komutlarını buraya ekleyebilirsiniz)'
            }
        }
    }

    post {
        success {
            echo 'Pipeline başarıyla tamamlandı!'
        }
        failure {
            echo 'Pipeline başarısız oldu.'
        }
    }
}
