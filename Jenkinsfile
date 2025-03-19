pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'master', url: 'https://github.com/DeepakPrakasam/Maven.git'
            }
        }
        stage('build') {
            steps {
               sh "mvn clean"
               sh "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t deepakp2003/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                  sh 'docker push deepakp2003/simplewebapp'
               }
            }
            }
}
}
}
