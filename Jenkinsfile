pipeline {
    agent any
    options {
      timeout(time: 60, unit: 'SECONDS') 
    }
    stages {
        stage('Package'){
            steps{
                script{
                	sh './mvnw clean package -e'
                }
            }

        }
        stage('sonarQube'){
        	steps{
        		script{
					    withSonarQubeEnv('sonar') {
					      sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
					    }
        		}
        	}
        }
        stage('Nexus Upload'){
            steps{
                nexusArtifactUploader artifacts:
                [
                    [
                        artifactId: 'DevOpsUsach2020', classifier: '', file: 'build/DevOpsUsach2020-1.0.1.jar', type: 'jar'
                    ]
                ],
                credentialsId: 'nexus-local',
                groupId: 'com.devopsusach2020',
                nexusUrl: 'http://localhost:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'test-nexus',
                version: '1.0.1'
            }
        }
    }
}
