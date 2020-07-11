pipeline {
    agent any
    tools {
        maven 'maven3'
    }

    stages{
        stage('Build'){
            steps{
                 bat script: 'mvn clean package'

            }
        }
        stage('Upload War To Nexus'){
            steps{
                script{


                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: "target/simple-app-1.0.0.war", 
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: 'http://localhost:8081/', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'simpleapp-release', 
                    version: '1.0.0'
                    }
            }
        }
    }
}
