pipeline {
    agent any
    options {
      timeout(time: 60, unit: 'SECONDS') 
    }
    stages {
        stage('Compile'){
            steps{
                dir ('/Users/imagemaker/Documents/DevOps/modulo3/ejemplo-maven'){
                    sh './mvnw clean compile -e'  
                }
            }
            
        }
        stage('Unit'){
            steps{
                dir ('/Users/imagemaker/Documents/DevOps/modulo3/ejemplo-maven'){
                    sh './mvnw clean test -e'  
                }
            }
        }
        stage('Jar'){
            steps{
                dir ('/Users/imagemaker/Documents/DevOps/modulo3/ejemplo-maven'){
                    sh './mvnw clean package -e'  
                }
            }
        }
        stage('Run'){
            steps{
                dir ('/Users/imagemaker/Documents/DevOps/modulo3/ejemplo-maven'){
                    sh 'nohup bash ./mvnw spring-boot:run &'
                }
            }
        }
        stage('Test'){
            steps{
                dir ('/Users/imagemaker/Documents/DevOps/modulo3/ejemplo-maven'){
                    sh 'curl -X GET "http://localhost:8080/rest/mscovid/test?msg=testing"'
                }
            }
        }
    }
}


