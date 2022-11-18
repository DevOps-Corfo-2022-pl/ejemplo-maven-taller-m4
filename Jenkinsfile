pipeline {
    agent any
    stages {
        stage('Inicio') {
            steps {
                echo 'Iniciando....'
            }
        } 
        stage('Compilación') {
            steps {
             git branch: 'main', url: 'https://github.com/DevOps-Corfo-2022-pl/ejemplo-maven-taller-m4.git'
                sh './mvnw clean compile -e'
            }
        }
        stage('Build'){
          steps{
                      sh './mvnw clean package'
          }
        }
        stage('Test') {
            steps {
                sh './mvnw clean test -e'
            }
        }
        stage('Jar Code') {
            steps {
                sh './mvnw clean package -e'
            }
        }
        stage('Run Jar') {
            steps {
                sh 'nohup bash mvnw spring-boot:run &'
            }
        }
        stage('SonarQube t2m4') {
  	  steps{
    		 withSonarQubeEnv(credentialsId: 'token-sonar', installationName: 'sq-taller2-m4') {
  		   sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar \
  		      -Dsonar.target=sonar.java.binaries'
   		}
  	  }
       }
    }
}
