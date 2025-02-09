pipeline {
    agent any

    stages {
        stage('Build the app') {
          agent{
            docker{
              image 'node:18-alpine'
              reuseNode true
            }
          }
            steps {
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }

        stage('testing the app') {
          agent{
            docker{
              image 'node:18-alpine'
              reuseNode true
            }
          }
          steps{
            sh'''
              test -f /build/index.html
              npm test
            '''
          }
        }
    }
}
