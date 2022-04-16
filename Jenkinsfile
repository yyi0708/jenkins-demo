pipeline{
    agent any
    environment { 
        CC = 'clang'
    }
    stages{
        stage("stage-A"){
            environment { 
                AN_ACCESS_KEY = credentials('my-prefined-secret-text') 
            }
            steps{
                checkout scm
                echo "========executing A========"
                sh 'printenv'
            }
        }
        stage("stage-B"){
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
        stage("stage-C"){
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}