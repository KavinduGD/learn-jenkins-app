pipeline {
    agent any

    stages {

        stage('pre') {
            agent {
                label 'master'    // force test stage to master
            }
            steps {
                sh '''
                touch test.txt
                '''
            }
        }

        stage('build') {
            agent {
                label 'slave-1'   // ensure this stage runs only on slave-1
            }
            steps {
                script {
                    docker.image('node:18-alpine').inside('-u root') {
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

        stage('test') {
            agent {
                label 'master'    // force test stage to master
            }
            steps {
                sh '''
                    hostname
                    ls -la
                    echo 'I am from master'
                '''
            }
        }
    }
}
