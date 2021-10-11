
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
                    repository: 'YOUR_REPO_NAME_IN_GCTS'
                ) 
            }
        }
		
	stage('gctsDeploy-XYZ') {
            steps {
                script {
                    try {
                        gctsDeploy(
                            host: 'HOST',
                            client: 'CLIENT',
                            abapCredentialsId: 'ABAPUserPasswordCredentialsId',
                            repository: 'YOUR_REPO_NAME_IN_GCTS',
                            //remoteRepositoryURL: "https://remote.repository.url.com",
                            //role: 'SOURCE',
                            vSID: 'XYZ',
                            //branch: 'branch',
                            //commit: 'commit',
                            //scope: 'scope',
                            //rollback: false,
                            //configuration: [dummyConfig: 'dummyval']
                        )
                    }
                    catch(all) {
                        echo "Error while Deploying SAP Objects in XYZ."
                        currentBuild.result = 'FALURE'
                    }
                }
            }
        }
}
}
