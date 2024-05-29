pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your version control system
                git 'https://github.com/harsanskumaran/jenkins-cicd.git'
            }
        }
        
        stage('Install dependencies') {
            steps {
                // Install Python dependencies using pip
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run tests') {
            steps {
                // Run your Python tests
                sh 'python3 -m unittest discover -s tests -p "*test.py"'
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
          emailext attachLog: true, attachmentsPattern: 'text', body: 'Hi Deployment successful! Please find the attached log FYR', subject: 'Deployment successful! ${currentBuild.fullDisplayName} ', to: 'harsanskumaran@gmail.com, svhkfood@gmail.com'       
        }
        
        failure {
          echo 'Deployment Failed!'
          emailext attachLog: true, attachmentsPattern: 'text', body: 'Hi Deployment Failed! Please find the log FYR', subject: 'Deployment Failed! ', to: 'harsanskumaran@gmail.com, svhkfood@gmail.com'        
        }
    }
}
