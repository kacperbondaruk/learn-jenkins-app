pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true   
                }
            }
            steps {
                sh '''
                    echo "Test stage"
                    if [-f build/index.html ]; then
                        echo "File Exists"
                    else
                        echo "File Doesn't Exists"
                    fi
                '''
            }

        }

    }
}