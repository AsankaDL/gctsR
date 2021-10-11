
@Library('piper-lib-os') _


pipeline {
    agent any
    stages {
        stage ('gctsExecuteABAPUnitTests') {
            steps {
		gctsExecuteABAPUnitTests (
                    //script: this,
                    host: 'http://narvi.xrsc.local:8000',
                    client: '200',
                    abapCredentialsId: 'ABAPUserPasswordCredentialsId',
                    repository: 'gctsR'
                ) 
            }
        }
		
	stage('gctsDeploy-VH1') {
            steps {
                script {
                    try {
                        gctsDeploy(
                            host: 'http://despina.xrsc.local:8000',
                            client: '400',
                            abapCredentialsId: 'ABAPUserPasswordCredentialsId',
                            repository: 'gctsR',
                            //remoteRepositoryURL: "https://remote.repository.url.com",
                            //role: 'SOURCE',
                            vSID: 'VH1',
                            //branch: 'branch',
                            commit: 'commit',
                            //scope: 'scope',
                            //rollback: false,
                            //configuration: [dummyConfig: 'dummyval']
                        )
                    }
                    catch(all) {
                        echo "Error while Deploying SAP Objects in VH1."
                        currentBuild.result = 'FALURE'
                    }
                }
            }
        }
}
}
