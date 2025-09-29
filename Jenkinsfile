pipeline{
    agent any

    stages{
        // stage('build'){
        //     agent{
        //         docker{
        //             image 'node:18-alpine'
        //             reuseNode true
        //             args '-u root' 
        //         }
        //     }
        //     steps{
        //         sh '''
        //             npm ci 
        //             npm run build
        //         '''
        //     }
        // }
        
        stage('test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                    args '-u root' 
                }
            }
            steps{
                sh '''
                    test -f public/index.html
                    npm ci 
                    npm test
                '''
            }
        }

        stage('e2e test'){
            agent{
                docker{
                    image 'mcr.microsoft.com/playwright:v1.55.0-noble'
                    reuseNode true
                    args '-u root' 
                }
            }
            steps{
                sh '''
                    npm i -g serve
                    server -s build
                    npx plawright test
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