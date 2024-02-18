pipeline {
    agent {
        node {
            label 'agent-1'
        }
    }
    environment { 
        MyENV = 'Hello Jenkins '
    }
    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()

    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                // submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins local', description: 'Who should I say hello to?')

                    text(name: 'BIOGRAPHY1', defaultValue: '', description: 'Enter some information about the person')

                    booleanParam(name: 'TOGGLE1', defaultValue: true, description: 'Toggle this value')

                    choice(name: 'CHOICE1', choices: ['One-local', 'Two-local', 'Three-local'], description: 'Pick something')

                    password(name: 'PASSWORD1', defaultValue: 'SECRET-local', description: 'Enter a password')
                }
            }
            steps {
                echo 'Building..'
                echo "Person name is: ${params.PERSON}"
                echo "Person name is: ${params.PERSON}"
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
                    #sleep 10
                '''
            }
        }
        stage('Example') {
            steps {
                echo "Hello ${PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
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