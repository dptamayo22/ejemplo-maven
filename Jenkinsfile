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
    }
}
