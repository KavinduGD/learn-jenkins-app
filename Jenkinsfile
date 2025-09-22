pipeline{
    agent { label 'slave-1' }

    stages{
        stage('Hello'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                    args '-u root' 
                }
            }
            steps{
                sh '''
                    ls -la
                    npm ci 
                    npm run build
                    ls -la
                '''
            }
        }
    }
}