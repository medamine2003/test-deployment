pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/medamine2003/test-deployment.git'
            }
        }
        stage('Build') {
            steps {
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                sh 'test -f index.html && echo "index.html trouvé"'
                sh 'test -f index.css && echo "index.css trouvé"'
            }
        }
        
    }
}