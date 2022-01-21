pipeline {
    agent any

    stages {
        stage('Nexus Download') {
            steps {
                script {
                    bat "curl -X GET -u admin:Pelusa50# http://localhost:8081/repository/test.nexus/com/devopsusach2020/DevOpsUsach2020/0.0.1/DevOpsUsach2020-0.0.1.jar -O"  
                    bat "dir" 
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
                    bat "start chrome http://localhost:8082/rest/mscovid/test?msg=testing"
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

