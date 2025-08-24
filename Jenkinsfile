@Library('piper-lib-os') _
pipeline {
    agent any

    stages {
        stage('Prepare') {
            steps {
                checkout scm
            }
        }

        stage('Upload Integration Artifact') {
            steps {
                withCredentials([string(credentialsId: 'service-key', variable: 'CPI_SERVICE_KEY_JSON')]) {
                    sh '''
                        printf "%s" "$CPI_SERVICE_KEY_JSON" > serviceKey.json

                        echo "Service key file size: $(wc -c < serviceKey.json) bytes"

                        piper integrationArtifactUpload \
                          --serviceKey serviceKey.json \
                          --integrationFlowId filter_iflow \
                          --integrationFlowFilePath filter_iflow.zip
                    '''
                }
            }
        }

        stage('Deploy Integration Artifact') {
            steps {
                withCredentials([string(credentialsId: 'service-key', variable: 'CPI_SERVICE_KEY_JSON')]) {
                    sh '''
                        printf "%s" "$CPI_SERVICE_KEY_JSON" > serviceKey.json

                        piper integrationArtifactDeploy \
                          --serviceKey serviceKey.json \
                          --integrationFlowId filter_iflow
                    '''
                }
            }
        }
    }
}
