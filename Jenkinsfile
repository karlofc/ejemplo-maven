pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
				bat 'mvnw.cmd clean compile -e'
            }
        }
		stage('Test') {
            steps {
				bat 'mvnw.cmd clean test -e'
            }
        }
		stage('Jar') {
            steps {
				bat 'mvnw.cmd clean package -e'
            }
        }
		stage('SonarQube analysis') {
			steps {
				withSonarQubeEnv(installationName: 'sonar') { // You can override the credential to be used
					bat 'mvnw.cmd sonar:sonar -Dsonar.projectKey=MOD3_EJE6 -Dsonar.host.url=http://localhost:9000 -Dsonar.login=75a0e9b0613f563c0e69a23174cf79eb5d4d74c7'
				}
			}
		}
		stage('Upload Nexus') {
			steps {
				nexusPublisher nexusInstanceId: 'nexus-maricel', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'C:\\Users\\carlo.figueroa\\.jenkins\\workspace\\3_EJE4_Multibranch_feature-nexus\\build\\DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
			}
		}
    }
}
