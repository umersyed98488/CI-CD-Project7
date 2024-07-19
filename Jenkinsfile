pipeline {
    agent any 
    tools {
        maven "maven"
    }
    stages {
        stage('clean') {
            steps {
                cleanWs()
            }
        }
        stage('code commit') {
            steps {
                git 'https://github.com/umersyed98488/CI-CD-Project7.git'
            }
        }
        stage('Integration test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
