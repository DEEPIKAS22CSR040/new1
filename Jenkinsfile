pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/Bavyadharshini-Rajaganapathy/devops1.git'
            }
        }
        stage('build') {
            steps {
               bat "mvn clean"
               bat "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t /simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                  sh 'docker push deepika040/simplewebapp'
               }
            }
            }
}
}
}