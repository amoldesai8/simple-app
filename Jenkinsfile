pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War To Nexus'){
            steps{
                script {
               nexusArtifactUploader artifacts: 
                   [
                   [
                    artifactId: 'simple-app', 
                    classifier: '', 
                    file: 'target/simple-app-1.0.0.war', 
                    type: 'war'
                   ]
                   ], 
                   credentialsId: 'NexusCreds', 
                   groupId: 'in.javahome', 
                   nexusUrl: 'localhost:8081/', 
                   nexusVersion: 'nexus3', 
                   protocol: 'http', 
                   repository: 'simpleapp', 
                   version: '1.0.0'
                }
            }
        }
    }
}
