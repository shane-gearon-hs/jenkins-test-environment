pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh "echo PASS"
            }
        }
        stage("Test") {
            steps {
                sh "echo TEST PASS"
            }
        }
        stage("Deploy") {
            steps {
                sh "fail"
            }
        }
    }
}