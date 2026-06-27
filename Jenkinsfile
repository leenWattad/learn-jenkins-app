pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                    ls -la
                    node --verion
                    npm --verion
                    npm ci
                    npm run build
                    ls -ls
                '''
            }
        }
    }
}
