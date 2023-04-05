pipeline {
    agent any
    environment {
        name = 'harkirat'
    }
    parameters{
        string(name: 'person', defaultValue: 'Shubham', description: 'String Parameter')
        booleanParam(name: 'ismale', defaultValue: true, description: "Is person Male or Not")
        choice(name: 'City', choices:['Jaipur','KKR','Mumbai'], description: "Which City ?")
    }
    stages {
        stage('Run a command in single step') {
            steps {
                sh '''
                ls
                pwd
                '''
            }
        }
        stage('Run a Command and Env Variables for a certain Stage') {
           environment {
             username = 'harkirat'
           }
            steps {
                sh 'echo "${username}"'
                sh 'date'
                sh 'pwd'
            }
        }
        stage('Continue ?') {
            input {
                message "Should I continue ?"
                ok "Yes we should"
            }
            steps {
                echo "Keep Going"
            }
        }
        stage('Print Environment Variables') {
            when {
                expression {
                    name == 'harkirat'
                }
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                sh 'echo "${person}"'
                sh 'echo "${ismale}"'
                sh 'echo "${City}"'
            }
        }
        stage('Success Stage') {
            steps {
                echo 'Harkirat'
            }
        }
    }
    post {
        always {
            echo 'I will always run'
        }
        failure {
            echo 'I will run when any stage fails'
        }
        success {
            echo 'I will run when all the stages are successful'
        }
    }
}
