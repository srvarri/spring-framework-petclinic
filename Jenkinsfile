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
                sh 'docker image build -t spc_two:1.0 .'
            }
        }
        stage('container run') {
            steps {
                sh 'docker container run -d --name spc -p 8081:8080 spc_two:1.0'
            }
        }
    }
}            