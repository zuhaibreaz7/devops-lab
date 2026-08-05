pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t devops-lab .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f devops-lab-container || true
                    docker run -d \
                      --name devops-lab-container \
                      -p 80:80 \
                      devops-lab
                '''
            }
        }
    }
}
