pipeline {
    agent { 
        docker {
            image 'maven:3.3.9'
            args '-v /root/.m2:/root/.m2'
        } 
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}
