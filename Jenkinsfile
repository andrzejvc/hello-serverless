pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                nodejs(nodeJSInstallationName: 'nodejs') {
                    sh 'npm install'
                    sh 'npm rebuild'
                    sh 'npm run build --skip-test --if-present'
                }
            }
        }
        stage('deploy') {
            steps {
                nodejs(nodeJSInstallationName: 'nodejs') {
                    withAWS(credentials: 'e8b9727a-01d7-46b0-8d77-0a40a2a69f06') {
                        sh 'serverless deploy'
                    }
                }
            }
        }
    }
}