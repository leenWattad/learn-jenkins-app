pipeline {
    agent any

    stages {
        /*
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -ls
                '''
            }
        }
        */

        stage('Test'){
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }

            steps {
                sh '''
                    #test -f build/index.html
                    npm test
                '''
                
            }
        }

        stage('E2E'){
            agent{
                docker{
                    image 'mcr.microsoft.com/playwright:v1.61.0-noble'
                }
            }

            steps {
                sh '''
                    npm install -g serve
                    serve -s build
                    npx playwrite test
                '''
                
            }
        }
    }

    post{
        always{
            junit 'test-results/junit.xml'
        }
    }
}
