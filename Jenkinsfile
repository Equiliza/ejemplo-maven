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
        stage('SonarQube analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner';
                    withSonarQubeEnv('sonar-server') {
                    bat "C:/Users/Patric~1/.jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonar-scanner/bin/sonar-scanner.bat -Dsonar.projectKey=ejemplo-maven-new2 -Dsonar.sources=src -Dsonar.java.binaries=build"
                    }
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

