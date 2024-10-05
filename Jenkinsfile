pipeline{
    agent any
    tools{
        maven 'my-maven'
        jdk 'my-jdk'
    }
    stages{
        stage('Clone'){
            steps{
                git url:'https://github.com/ArchitAvd/employee-service',branch:'master'
            }
        }
        stage('Build'){
            steps{
                bat "mvn clean install -DskipTests"
            }
        }
        stage('Test'){
            steps{
                bat "mvn test"
            }
        }
        stage('Deploy'){
            steps{
                bat "docker rm -f my-empl-container"
                bat "docker rmi -f my-empl-image"
                bat "docker build -t my-empl-image ."
                bat "docker run -p 8082:8082 -d --name my-empl-container my-empl-image"
            }
        }
    }
}