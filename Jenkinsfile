pipeline {
    agent none  

    stages {
        stage('Check Docker') {
            agent { 
                docker { 
                    image 'maven:3.9.9-eclipse-temurin-21-alpine' 
                    args '--entrypoint=""' 
                } 
            }
            steps {
                sh 'docker --version || echo "Docker not found!"'
            }
        }

        stage('Build') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                sh 'mvn --version'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps work too"
                    ls -lah
                '''
            }
        }
        // stage('Run Node.js') {
        //     agent { docker { image 'node:22.14.0-alpine3.21' } }
        //     steps {
        //         sh 'node --version'
        //         sh 'npm install'
        //     }
        // }
    }

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
