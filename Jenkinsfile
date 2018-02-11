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
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
            post {
               always {
                  jacoco classPattern: '**/target/classes', execPattern: '**/target/**.exec'
               }
            }
       }
    }
}
