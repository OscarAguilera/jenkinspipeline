pipeline {
    agent { label 'slave' }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        choice(choices: ['deploy' , 'skip'], description: 'Description nothing else', name: 'REQUESTED_ACTION')
        booleanParam(name: 'Prod_Deploy', defaultValue: false, description: '')
    }
    stages {
        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"
            }
        }
        stage('Sonarqube') {
            steps {
                echo "Stage SonarQube"
            }
        }

        stage('Build'){
            steps {
                echo "Stage Build"
            }
        }

        stage('Liquibase'){
            steps {
                echo "Stage LiquiBase"
            }
        }

        stage ('Deploy'){
            when {
                branch 'prod'
                expression { params.REQUESTED_ACTION == 'deploy' && env.BRANCH_NAME == 'prod' && params.Prod_Deploy == 'true'}
            }
             steps {
                echo "Stage LiquiBase"
            }
        }
    }
}