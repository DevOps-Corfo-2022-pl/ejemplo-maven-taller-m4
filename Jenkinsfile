pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Compilación') {
            steps {
	     git branch: 'main', url: 'https://github.com/paulolagosg/ms-iclab-g5.git'
                sh './mvnw clean compile -e'
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
   		 withSonarQubeEnv(credentialsId: 'token-sq', installationName: 'sq-taller2-m4') {
  			sh 'mvn org.sonarsource.scanner.maven:sonar-maven-pulgin:3.7.0.1746:sonar \
  				-Dsonar.target=sonar.java.binaries'
   		}
  	}
}
    }
}
