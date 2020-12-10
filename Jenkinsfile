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
        stage('Nexus Upload'){
            steps {
                nexusArtifactUploader(
                nexusVersion: 'nexus3',
                protocol: 'http',
                nexusUrl: 'localhost:8081',
                groupId: 'com.devopsusach2020',
                version: '1.0.0',
                repository: 'test-nexus',
                credentialsId: 'nexus-local',
                artifacts: [
                    [artifactId: 'DevOpsUsach2020',
                    classifier: '',
                    file: 'build/DevOpsUsach2020-0.0.1.jar',
                    type: 'jar']
                ]
                )
            }
        }
    }
}
