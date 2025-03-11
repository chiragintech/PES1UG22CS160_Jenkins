pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'g++ -o new new.cpp'
                sh 'curl -X POST http://localhost:8080/job/PES1UG22CS160-1/build'
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
