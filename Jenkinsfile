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
                sh 'aws s3 cp $WORKSPACE/target/*.war s3://b-90-adv-docker-k8-terraform-projects/LoginRegisterApp-$BUILD_NUMBER.war'
            }
        }
        stage('Build Docker Image') {
            steps{
                sh ''' cd $WORKSPACE '''
                sh ''' docker build -t syedumer17/loginregisterapp:$BUILD_NUMBER .'''
            }
        }
        stage('Registery Login'){
            steps{
                withCredentials([usernamePassword(credentialsId: '7', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
                    sh 'docker login -u $USERNAME -p $PASSWORD'
            }
        }
        stage('push Docker Image') {
            steps{
                sh '''docker build -t syedumer17/loginregisterapp:$BUILD_NUMBER .'''
            }
        }
    }
}
