pipeline {
    agent any
    parameters {
        string(
            name: 'email', 
            defaultValue: 'test@ttt.com', 
            description: 'Email address to send notification' )
    }
    stages{
        stage("build") { 
            steps {
                echo "run npm i"
            }
        }
        stage("test") { 
            steps {
                echo "test runed"
            }
        }
        stage("deploy") { 
            steps {
                echo "deploy runed"
            }
        }
    }

    post {
        failure {
            mail(
                to: "${params.email}",
                subject: "${JOB_NAME}.${BUILD_NUMBER} FAILED",
                body: "${JOB_NAME}.${BUILD_NUMBER} FAILED"
            )
        }
        success {
            mail(
                to: "${params.email}",
                subject: "${JOB_NAME}.${BUILD_NUMBER} PASSED",
                body: "${JOB_NAME}.${BUILD_NUMBER} PASSED"
            )
        }
    }
}