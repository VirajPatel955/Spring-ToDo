pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'mvn clean test'
            }
        }
        stage('Build') {
            steps {
                sh '''
                mvn clean install
                mv ./target/*.war /jenkins/project-wars/project-${BUILD_NUMBER}.war
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                java -jar /jenkins/project-wars/project-${BUILD_NUMBER}.war
                '''
            }
        }
    }
}
