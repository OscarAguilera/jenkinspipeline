pipeline {
    agent { label 'slave' }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?'),
        choice(
            choices: ['deploy' , 'skip'],
            description: '',
            name: 'REQUESTED_ACTION')
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
                //branch 'prod'
                expression { params.REQUESTED_ACTION == 'greeting' }
            }
            steps {
                echo "Stage Deploy"
            }
        }
    }
}