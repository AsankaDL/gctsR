
@Library('piper-lib-os') _


pipeline {
    agent any
    stages {
        stage ('gctsExecuteABAPUnitTests') {
            steps {
		gctsExecuteABAPUnitTests (
                    //script: this,
                    host: 'HOST',
                    client: 'CLIENT',
                    abapCredentialsId: 'ABAPUserPasswordCredentialsId',
                    repository: 'gctsR'
                ) 
            }
        }
		
	stage('gctsDeploy-VGT') {
            steps {
                script {
                    try {
                        gctsDeploy(
                            host: 'HOST',
                            client: 'CLIENT',
                            abapCredentialsId: 'ABAPUserPasswordCredentialsId',
                            repository: 'gctsR',
                            //remoteRepositoryURL: "https://remote.repository.url.com",
                            //role: 'SOURCE',
                            vSID: 'VGT',
                            //branch: 'branch',
                            //commit: 'commit',
                            //scope: 'scope',
                            //rollback: false,
                            //configuration: [dummyConfig: 'dummyval']
                        )
                    }
                    catch(all) {
                        echo "Error while Deploying SAP Objects in VGT."
                        currentBuild.result = 'FALURE'
                    }
                }
            }
        }
}
}
