pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
                git branch: 'main', url: 'https://github.com/DEEPIKAS22CSR040/new1.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean'
                sh 'mvn install'
            }
        }
        stage('build to images') {
            steps {
                script {
                    sh 'docker build -t deepika040/mysimplewebapplication .'
                }
            }
        }
        stage('push to hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-hub-credential', url: 'https://index.docker.io/v1/') {
                        sh 'docker push deepika040/mysimplewebapplication'
                    }
                }
            }
        }
    }
}
