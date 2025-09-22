pipeline{
    agent any

    stages{
        stage('build'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                    args '-u root' 
                }
            }
            steps{
                sh '''
                    npm ci 
                    npm run build
                '''
            }
        }
        
        stage('test'){
            steps{
                sh '''
                    file -f public/index.html
                    npm test'
                '''
            }
        }
    }
}