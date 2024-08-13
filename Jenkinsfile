pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Setting up Python environment...'
                    sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                    '''
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    sh '''
                    . venv/bin/activate
                    python -m unittest discover -s tests
                    '''
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying the application...'
                    sh '''
                    . venv/bin/activate
                    ssh -i /path/to/your/key.pem ubuntu@your-ec2-public-ip << EOF
                        cd /path/to/your/app
                        git pull origin main
                        pip install -r requirements.txt
                        sudo systemctl restart your-app-service
                    EOF
                    '''
                }
            }
        }
    }
}
