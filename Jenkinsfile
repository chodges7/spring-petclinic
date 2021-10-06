
pipeline {
    agent any
    environment {
        ADMIN_TOKEN = credentials('artifactory-admin-token')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh "./mvnw package"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh "./mvnw test"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'curl -u jenkins:$ADMIN_TOKEN -X PUT "http://artifactory:8081/artifactory/maven-artifactory/petclinic/spring-petclinic-2.5.0-SNAPSHOT.jar" -T target/spring-petclinic-2.5.0-SNAPSHOT.jar'
            }
        }
    }
}
