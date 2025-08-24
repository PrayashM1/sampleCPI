@Library('piper-lib-os') _   // SAP Jenkins library

pipeline {
    agent any

    stages {
        stage('Prepare') {
            steps {
                checkout scm
                setupCommonPipelineEnvironment script: this
            }
        }

        stage('Upload IFlow') {
            steps {
                integrationArtifactUpload script: this
            }
        }

        stage('Deploy IFlow') {
            steps {
                integrationArtifactDeploy script: this
            }
        }
    }
}
