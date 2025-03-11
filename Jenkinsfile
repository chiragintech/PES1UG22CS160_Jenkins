pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'g++ -o new new.cpp'
                build 'PES1UG22CS160-1'
            }
        }
        stage('Test') {
            steps {
                sh './new'
            }
        }
        stage('Deploy') {
            steps {
                sh 'git add . && git commit -m "New cpp file" && git push'
            }
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
