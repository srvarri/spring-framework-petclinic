pipeline {
    agent any
        stages {
            stage('vcs') {
                   steps {
                       git branch: 'REL_INT_1.0',
                       url: 'https://github.com/srvarri/spring-framework-petclinic.git'
                       
                    }
                }
        stage('JFROG configuration') {
                    steps {
                        rtMavenDeployer (
                            id: "MVN_DEFAULT",
                            serverId: "JFROG_SPC",
                            releaseRepo: "spc1-libs-release-local",
                            snapshotRepo: "spc1-libs-snapshot-local"
                        )
                    }
                }
                
        stage('maven build') {
                    steps {
                        rtMavenRun (
                            tool: "maven", // Tool name from Jenkins configuration
                            pom: "pom.xml",
                            goals: "clean install",
                            deployerId: "MVN_DEFAULT"
                            
                        )
                    }
                }
                
        stage ('publish build info') {
                    steps {
                        rtPublishBuildInfo (
                            serverId: "JFROG_SPC"
                        )
                    }
        }
    }
}