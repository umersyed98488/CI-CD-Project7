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
        stage('Artifactory') {
            steps{
                sh 'aws s3 cp $WORKSPACE/target/*.war s3://b90-artifactory/loginregisterapp-$BUILD_NUMBER.war'
            }
        }
    }
}
