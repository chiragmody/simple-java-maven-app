pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 1
            steps {
                sh 'mvn test' 2
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 3
                }
            }
        }
    }
}
