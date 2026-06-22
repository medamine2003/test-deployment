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
        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f test-deployment-site || true
                    docker run -d --name test-deployment-site --network devops -p 8081:80 nginx:alpine
                    sleep 2
                    docker cp $WORKSPACE/. test-deployment-site:/usr/share/nginx/html/
                '''
            }
        }
    }
}