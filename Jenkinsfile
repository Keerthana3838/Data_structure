pipeline {
    agent any

    stages {
        stage('CHECKOUT CODE') {
            steps {
                git credentialsId : 'PATDemo', url : 'https://github.com/Keerthana3838/Data_structure.git', branch : 'master'
            }
            
        }

        stage('Install dependencies') {
            steps {
                bat '''
                python -m venv venv 
                call venv\\Scripts\\activate
                pip install --upgrade pip
                pip install pytest
                '''
            }
            
        }

        stage('Run python scripts') {
            steps {
                bat '''
                    venv\\Scripts\\activate
                    pytest test.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying feature'
            }
        }
    }

    post {
        success {
            echo 'pipeline succeded'
        }
        failure {
            echo 'pipeline failed'
        }
    }
}