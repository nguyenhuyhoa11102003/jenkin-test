pipeline {
    agent any
    tools {
        maven 'Maven 3.9.9'  // Tên Maven đã cấu hình trong Jenkins
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sh 'echo Hello world'
                sh '''
                    echo "Multiline shell steps works too1"
                    ls -lah
                '''
            }
        }
    }
}
