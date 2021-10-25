
pipeline {
    agent any
    environment {
        ADMIN_TOKEN = credentials('artifactory-admin-token')
        VERSION = readMavenPom().getVersion()
    }
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling...'
                sh "./mvnw compile" // or sh "mvn compile"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh "./mvnw test" // or sh "mvn test"
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging...'
                sh "./mvnw package -Dmaven.test.skip" // or sh "mvn package"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'curl -u jenkins:$ADMIN_TOKEN -X PUT "http://artifactory:8081/artifactory/maven-artifactory/petclinic/spring-petclinic-2.5.0-SNAPSHOT.jar" -T target/spring-petclinic-$VERSION.jar'
            }
        }
    }
}
