pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('Sonar Analysis') {
            environment {
                scannerHome = tool 'SONAR_SCANNER'
            }
            steps {
                withSonarQubeEnv('SONAR_LOCAL') {
                    sh "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=ProjetoBack -Dsonar.host.url=http://127.0.0.1:9000 -Dsonar.login=c4b18e6c6caef2fb5271806770a03b69abbb75b3 -Dsonar.java.binaries=target"
                }
            }
        }
    }
}

