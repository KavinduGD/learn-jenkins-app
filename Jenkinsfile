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
                    sudo npm ci 
                    npm run build
                    ls -la
                '''
            }
        }
    }
}