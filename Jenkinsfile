pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                // Nettoyer le projet
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
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('Nom_de_votre_instance_SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
