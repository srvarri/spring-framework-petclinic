pipeline {
    agent  { label 'JDK11' }
    stages {
        stage('vcs') {
            steps {
                git branch: 'master', url: 'https://github.com/srvarri/spring-framework-petclinic.git'
            }

        }
        stage('image build') {
            steps {
                sh ' docker image build -t spc_two:1.0 .'
                ///sh sudo chown ubuntu:ubuntu unix:///var/run/docker.sock
            
            }
        }
        stage('container run') {
            steps {
                sh ' docker container run -d --name spctwo -p 8082:8080 spc_two:1.0'
            }
        }
    }
}            