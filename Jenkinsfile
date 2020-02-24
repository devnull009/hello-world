pipeline {
    agent any

    stages {
        stage('Check requirements') {
            steps {
                sh 'which java'
                sh 'which javac'
            }
        }
        stage('Build') {
            steps {
                sh 'javac src/main/java/App.java'
            }
        }
        stage('Test') {
            steps {
                sh 'cd src/main/java && java App'
            }
        }
        stage('Prepare for deployment') {
            steps {
                sh 'tar cvf App.tar src/main/java/*.class'
                sh 'ls -l App.tar'
                sh 'tar tvf App.tar'
            }
        }
    }
}