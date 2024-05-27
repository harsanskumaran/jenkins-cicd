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
            script {
                def consoleOutput = currentBuild.rawBuild.getLog(10).join("\n")
                emailext subject: 'Pipeline Status - Success',
                         body: "Your pipeline has been successfully deployed.\n\nConsole Output:\n${consoleOutput}",
                         to: 'svhkfood@gmail.com'
            }
        }
        failure {
            // Notify on deployment failure
            echo 'Deployment failed!'
            script {
                def consoleOutput = currentBuild.rawBuild.getLog(10).join("\n")
                emailext subject: 'Pipeline Status - Failure',
                         body: "Your pipeline has failed to deploy.\n\nConsole Output:\n${consoleOutput}",
                         to: 'svhkfood@gmail.com'
            }
        }
    }
}
