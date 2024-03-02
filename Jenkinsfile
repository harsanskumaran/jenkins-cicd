pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your version control system
                git 'https://github.com/muthuramanathanm/jenkins-cicd.git'
            }
        }
        
        stage('Install dependencies') {
            steps {
                // Install Python dependencies using pip
                //sh 'python3 -m pip install -r requirements.txt'
                //sh '/usr/local/bin/pip install -r requirements.txt'
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run tests') {
            steps {
                // Run your Python tests
                sh 'python3 -m unittest discover -s tests -p "*_test.py"'
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy your Python application
                sh 'python3 HelloWorld.py'
            }
        }
    }
    
    post {
        success {
            // Notify on successful deployment
            echo 'Deployment successful!'
            emailext subject: 'Pipeline Status - Success',
                      body: 'Your pipeline has been successfully deployed.',
                      to: 'muthuramanathan.manickam@gmail.com'
        }
        failure {
            // Notify on deployment failure
            echo 'Deployment failed!'
            emailext subject: 'Pipeline Status - Failure',
                      body: 'Your pipeline has failed to deploy.',
                      to: 'muthuramanathan.manickam@gmail.com'
        }
    }

}

