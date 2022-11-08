pipeline {
    agent { label 'JDK11' }
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
                            id: 'MAVEN_DEPLOYER',
                            serverId: 'JFROG_SPC',
                            releaseRepo: 'spcc-libs-release-local',
                            snapshotRepo: 'spcc-libs-snapshot-local'
                        )
                    }
                }
                
        stage('maven build') {
                    steps {
                        rtMavenRun (
                            tool: 'MAVEN', // Tool name from Jenkins configuration
                            pom: 'pom.xml',
                            goals: 'clean install',
                            deployerId: "MAVEN_DEPLOYER"
                            
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