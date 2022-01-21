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
	stage('Nexus Upload') {
            steps {
		    nexusPublisher nexusInstanceId: 'test-nexus', nexusRepositoryId: 'test.nexus',
		    packages: [[$class: 'MavenPackage',
			mavenAssetList: [[classifier: '',
			extension: '',
			filePath: 'C:/Users/Patric~1/Desktop/Ejercicio/ejemplo-maven/build/DevOpsUsach2020-0.0.1.jar']],
			mavenCoordinate: [artifactId: 'DevOpsUsach2020',
			groupId: 'com.devopsusach2020',
			packaging: 'jar',
			version: '1.0.0']
			]]
            }
	}
    }
}

