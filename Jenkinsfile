pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {

                git 'https://github.com/ISTQB-Tester-Training/2021-11-CTAL-ATT-Online-Intern-ContinuousIntegration-Showcase.git'

                sh "mvn compile"
            }
        }
        stage('Unit Tests TDD') {
            steps {

                sh "mvn test -P TDD"
            }
        }
        stage('Code Analysis') {
            steps {

                sh "mvn sonar:sonar -Dsonar.host.url=http://ctp-tester-training.tk:30002/"
            }
        }
        stage('Behavior Tests BDD') {
            steps {

               sh "mvn test -P BDD"
            }
        }
        stage('Deploy to Local Repository') {
            steps {

                sh "mvn package -DskipTests"
            }
        }
        stage('Deploy to Remote Repository') {
            steps {

                sh "mvn deploy -DskipTests"
            }
        }
    }
}
