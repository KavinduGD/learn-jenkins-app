pipeline{
    agent any

    environment{
        NETLIFY_SITE_ID='b970c930-5c09-4899-8306-c8364ce73b45'
        NETLIFY_AUTH_TOKEN=credentials('netlify-token')
    }

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
        
        // stage('test'){
        //     agent{
        //         docker{
        //             image 'node:18-alpine'
        //             reuseNode true
        //             args '-u root' 
        //         }
        //     }
        //     steps{
        //         sh '''
        //             test -f public/index.html
        //             npm ci 
        //             npm test
        //         '''
        //     }
        // }

        // stage('e2e test'){
        //     agent{
        //         docker{
        //             image 'mcr.microsoft.com/playwright:v1.48.1-noble'
        //             reuseNode true
        //             args '-u root' 
        //         }
        //     }
        //     steps{
        //         sh '''
        //             npm i  serve
        //             node_modules/.bin/serve -s build &
        //             sleep 10
        //             npx playwright test --reporter=html
        //         '''
        //     }
        // }

    stage('Deploy'){
    agent{
        docker{
            image 'node:18-alpine'
            reuseNode true
            args '-u root' 
        }
    }
    steps{
        sh '''
            npm install netlify-cli@20.1.1
            node_modules/.bin/netlify --version
            echo $NETLIFY_SITE_ID
            node_modules/.bin/netlify status
        '''
    }
}
    }

   
}