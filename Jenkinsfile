pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the application...'
                    sh '/usr/bin/pip3 install -r requirements.txt'  // Adjust the path to pip
                }
            }
        }
        // Other stages...
    }
}
