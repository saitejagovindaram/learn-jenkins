pipeline {
    agent {
        node {
            label 'agent-1'
        }
    }
    environment { 
        MyENV = 'Hello Jenkins'
    }
    options {
        timeout(time: 1, unit: 'SECONDS') 
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('last') {
            steps {
                sh '''
                    echo 'hello'
                    env
                    echo "$MyENV"
                    sleep 10
                '''
            }
        }
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        success {
            echo 'I will say Hello when success!'
        }
        failure {
            echo 'I will say Hello when failure!'
        }
    }
}