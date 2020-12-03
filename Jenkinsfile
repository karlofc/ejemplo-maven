pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
				dir('D:\\cfigueroa\\Capital Humano\\Especialista DevOps\\Programas Alumnos\\repos_git\\ejemplo-maven-jenkins') {
					bat 'mvnw.cmd clean compile -e'
				}
            }
        }
		stage('Test') {
            steps {
                dir('D:\\cfigueroa\\Capital Humano\\Especialista DevOps\\Programas Alumnos\\repos_git\\ejemplo-maven-jenkins') {
					bat 'mvnw.cmd clean test -e'
				}
            }
        }
		stage('Jar') {
            steps {
                dir('D:\\cfigueroa\\Capital Humano\\Especialista DevOps\\Programas Alumnos\\repos_git\\ejemplo-maven-jenkins') {
					bat 'mvnw.cmd clean package -e'
				}
            }
        }
		stage('SonarQube analysis') {
			steps {
				dir('D:\\cfigueroa\\Capital Humano\\Especialista DevOps\\Programas Alumnos\\repos_git\\ejemplo-maven-jenkins') {
					bat 'mvnw.cmd clean package -e'
				}
				withSonarQubeEnv() { // You can override the credential to be used
					bat 'mvn sonar:sonar -Dsonar.projectKey=MOD3_EJE6 -Dsonar.host.url=http://localhost:9000 -Dsonar.login=75a0e9b0613f563c0e69a23174cf79eb5d4d74c7'
				}
			}
		}
		stage('Run') {
			steps {
				dir('D:\\cfigueroa\\Capital Humano\\Especialista DevOps\\Programas Alumnos\\repos_git\\ejemplo-maven-jenkins') {
					bat 'start mvnw.cmd spring-boot:run'
				}
			}
		}
		stage('Testing') {
			steps {
			    sleep 10
				bat 'curl http://localhost:8081/rest/mscovid/estadoMundial'
			}
		}
    }
}