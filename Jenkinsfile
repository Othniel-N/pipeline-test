pipeline {
    agent { label 'docker-compose' }
    stages {
        stage("Verifying installation"){
            steps {
                sh '''
                  docker version
                  docker info
                  docker-compose version
                  curl --version
                '''
            }
        }

        stage('Starting container'){
            steps {
                sh 'docker-compose -f docker-compose.yaml -p test build'
                sh 'docker-compose ps'
            }
        }

        stage('Testing against the container'){
            steps {
                sh 'curl http://194.238.19.169:3000/param?query=demo'
            }
        }
    }
}
