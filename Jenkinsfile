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
	     git branch: 'main', url: 'https://github.com/paulolagosg/ms-iclab-g5.git'
                sh './mvnw clean compile -e'
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
