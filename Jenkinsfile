pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                    bat "./mvnw.cmd clean compile -e"                       
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    bat "./mvnw.cmd clean test -e"                       
                }
            }
        }
        stage('Jar') {
            steps {
                script {
                    bat "./mvnw.cmd clean package -e"                       
                }
            }
        }
        stage('Run') {
            steps {
                script {
                    bat "start /min mvnw spring-boot:run &"
                    sleep 20
                }
            }
        }
        stage('TestApp') {
            steps {
                    bat "start chrome http://localhost:8081/rest/mscovid/test?msg=testing"
            }
        }
    }
}

