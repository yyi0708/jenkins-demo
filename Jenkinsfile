pipeline{
    agent any
    stages{
        stage("stage-A"){
            steps{
                echo "========executing A========"
                echo "1234"
            }
        }
        stage("stage-B"){
            input {
                message "Should we continue?"
                ok "Yes, we should do."
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
            echo "========always12========" 
            echo "========always12========" 
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}