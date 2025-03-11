pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '/main']],
                    userRemoteConfigs: [[url: 'https://github.com/chiragintech/PES1UG22CS160_Jenkins.git']]
                ])
            }
        }

        stage('Build') {
            steps {
                build 'PES1UG22CS160-1'
                sh 'g++ main.cpp -o output'

            }
        }
        stage('Test') {
            steps {
                sh './output'

            }
        }
        stage('Deploy') {
            echo 'Deploying the application...'
        }
    }
    post {
        always {
            script {
                currentBuild.result = currentBuild.result ?: 'SUCCESS'
            }
        }
        failure {
            echo 'pipeline failed'
        }
    }
}
