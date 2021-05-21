pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'printenv | sort'
                echo 'Building...'
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
