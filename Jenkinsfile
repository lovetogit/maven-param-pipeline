pipeline {
    agent any
    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'test', 'prod'], description: 'Choose environment to deploy')
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Code already present in workspace."
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (params.ENVIRONMENT == 'dev') {
                        sh './scripts/deploy-dev.sh'
                    } else if (params.ENVIRONMENT == 'test') {
                        sh './scripts/deploy-test.sh'
                    } else if (params.ENVIRONMENT == 'prod') {
                        sh './scripts/deploy-prod.sh'
                    }
                }
            }
        }
    }
}
