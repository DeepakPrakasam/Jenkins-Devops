pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/DeepakPrakasam/Jenkins-Devops.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t deepakp2003/simplewebapp .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'jenkins_token', url: 'https://index.docker.io/v1/') {
                        sh 'docker push deepakp2003/simplewebapp'
                    }
                }
            }
        }
    }
}
