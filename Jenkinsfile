pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u 0:0' // Run as the Jenkins user inside the container (using your provided UID and GID)
        }
    }
    stages {
        stage('Preparation') {
            steps {
                sh 'echo "Setting up permissions for npm cache"'
                sh 'mkdir -p /home/node/.npm && chown -R 115:121 /home/node/.npm || true' // Workaround for npm cache issue
                sh 'npm config set cache /home/node/.npm' // Adjusted the path based on typical Node.js Docker image structure
            }
        }
        stage('Build') {
            steps {
                sh 'npm install --save'
            }
        }
    }
}

