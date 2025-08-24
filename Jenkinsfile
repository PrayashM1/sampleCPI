@Library('piper-lib-os') _

node() {
    stage('Validate Secret') {
        // Run the simplest CPI step - Get MPL Status
        integrationArtifactGetMplStatus script: this, juStabUtils: utils, config: [
            host           : 'https://uat-2fp4a4tq.it-cpitrial05-rt.cfapps.us10-001.hana.ondemand.com',
            credentialsId  : 'service-key',
            integrationFlowId: 'filter_iflow'
        ]
    }
}
