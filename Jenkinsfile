pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Pushed by ${env.BBS_ACTOR}"
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
