pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/username/repository.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-streamlit-app")
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8501:8501 --name my-streamlit-app-container my-streamlit-app'
                }
            }
        }
    }
    
    post {
        always {
            script {
                // Hentikan dan hapus container setelah selesai
                sh 'docker stop my-streamlit-app-container || true'
                sh 'docker rm my-streamlit-app-container || true'
                cleanWs()
            }
        }
    }
}
