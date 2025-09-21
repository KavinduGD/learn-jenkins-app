pipeline{
    agent any

    stages{
        stage('Hello'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    ls -la
                    npm config set cache /tmp/npm-cache --global
                    npm ci 
                    npm run build
                    ls -la
                '''
            }
        }
    }
}