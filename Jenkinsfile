pipeline {
    agent  { label 'JDK11' }
    stages {
        stage('vcs') {
            steps {
                git branch: 'master', url: 'https://github.com/srvarri/spring-framework-petclinic.git'
            }

        }
        stage('build') {
            steps {
                sh 'ansible-playbook -i hosts learn.yaml'
            }
        }
    }
}            