pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
				git branch: 'main', credentialsId: 'cabbdcc2-ae95-42d9-a016-50786bff5726', url: 'https://github.com/PradeshCnx/nexusRepo.git'
				bat "mvn -Dmaven.test.failure.ignore-true clean package"
			}
		}
		stage('Upload War to Nexus'){
			steps{
				nexusArtifactUploader artifacts: [
				[
				artifactId: 'nexus-demo',
				classifier: '',
				file: 'target/nexus-demo-1.0.0-mule-application',
				type: 'war'
				]
				], 
				credentialsId: 'nexus',
				groupId: 'com.mycompany',
				nexusUrl: 'localhost:8081/nexus',
				nexusVersion: 'nexus3',
				protocol: 'http',
				repository: 'sampleApp-release',
				version: '1.0.0'
			}
		}
	}

}
