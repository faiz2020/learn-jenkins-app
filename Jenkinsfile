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
                script {
                    sh '''
                        echo "Listing files before build:"
                        ls -la

                        echo "Node and NPM versions:"
                        node --version
                        npm --version

                        echo "Installing dependencies:"
                        npm ci

                        echo "Running build:"
                        npm run build

                        echo "Listing files after build:"
                        ls -la
                    '''
                }
            }
        }
    }
}