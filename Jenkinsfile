pipeline {
    agent any

    environment {
        PROJECT_DIR = "redis-cluster"
    }

    stages {
        stage('Build Redis Cluster') {
            steps {
                sh '''
                docker-compose -f docker-compose.yml up -d
                sleep 10
                docker exec redis-cluster redis-cli -c -a redis init
                '''
            }
        }

        stage('Check Cluster') {
            steps {
                sh 'docker ps'
                sh 'docker logs redis-cluster'
            }
        }
    }
}
