pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/muzafferkoluman/wildrydes-site.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                # Buraya dağıtım komutlarınızı ekleyin
                # Örneğin, build dizinini bir sunucuya taşıyabilirsiniz.
                '''
            }
        }
        stage('Debug PATH') {
            steps {
                sh 'echo $PATH'
         }
}

    }

    post {
        success {
            echo 'Pipeline başarıyla tamamlandı!'
        }
        failure {
            echo 'Pipeline başarısız oldu!'
        }
    }
}
