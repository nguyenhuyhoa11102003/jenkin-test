pipeline {
    agent { 
        docker { 
            image 'maven:3.9.9-eclipse-temurin-21-alpine' 
            args '--entrypoint=""' 
        } 
    }
    
    stages {
        stage('Check Docker') {
            steps {
                sh 'docker --version || echo "Docker not found!"'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps work too"
                    ls -lah
                '''
            }
        }
    }

    // 🔥 `post` phải đặt bên trong `pipeline`, KHÔNG ĐƯỢC đặt trong `stages`
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
