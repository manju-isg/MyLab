pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Stage3 for deploying the artifacts to Sonar Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: '135f9dca-6b88-44fe-bce6-fa8d702d05a5', groupId: 'com.vinaysdevopslab', nexusUrl: '18.219.87.181:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'ManjuDevOpsLab-SNAPSHOT', version: '0.0.4-SNAPSHOT'
            }

        }

        // Stage3 : Publish the source code to Sonarqube
        /*stage ('Sonarqube Analysis'){
            steps {
                echo ' Source code published to Sonarqube for SCA......'
                withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
                     sh 'mvn sonar:sonar'
                }

            }
        }*/

        
        
    }

}
