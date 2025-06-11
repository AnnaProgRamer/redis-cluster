pipeline {
    agent any

    environment {
        PROJECT_DIR = "redis-cluster"
    }

    stages {
        stage('Start Redis Cluster') {
            steps {
                dir("${PROJECT_DIR}") {
                    sh '''
                    docker-compose up -d
                    '''
                }
            }
        }

        stage('Check Containers') {
            steps {
                dir("${PROJECT_DIR}") {
                    sh 'docker ps'
                    sh 'docker logs redis-master'
                }
            }
        }
    }
}
