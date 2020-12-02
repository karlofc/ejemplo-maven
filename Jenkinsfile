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