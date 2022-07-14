pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
				git branch: 'main', credentialsId: 'cabbdcc2-ae95-42d9-a016-50786bff5726', url: 'https://github.com/PradeshCnx/mule4Test.git'
				bat "mvn -Dmaven.test.failure.ignore-true clean package"
			}
		}
		stage('Upload War to Nexus'){
			steps{
				nexusArtifactUploader artifacts: [
				[
				artifactId: 'aws_s3_buckect',
				classifier: '',
				file: 'target/aws_s3_buckect',
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
