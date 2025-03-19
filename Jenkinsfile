pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/DeepakPrakasam/Maven.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
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
                    withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                        sh 'docker push deepakp2003/simplewebapp'
                    }
                }
            }
        }
    }
}
