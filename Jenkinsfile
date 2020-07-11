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
    }
}
