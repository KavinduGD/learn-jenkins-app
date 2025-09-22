pipeline{
    agent any

    stages{
        stage('build'){
            agent{
                docker{
                    image 'node:18-alpine'
                    label 'slave-1'
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
        
        stage('test'){
            steps{
                sh '''
                    ls -la
                    echo 'im from master'
                '''
            }
        }
    }
}