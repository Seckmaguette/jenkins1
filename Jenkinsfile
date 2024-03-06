pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                // Clean the project
                sh 'mvn -B clean'
            }
        }
         stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: '*/test-results/.xml'
                }
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}
