pipeline {
    agent {
        docker {
            image 'python:3.9-slim'
        }
    }
    environment {
        PYTHON_SCRIPT = 'main.py'
    }
    stages {
        stage('Initialize') {
            steps {
                echo 'Initializing environment...'
                sh 'python3 --version'
            }
        }

        stage('Execute Script') {
            steps {
                echo 'Running the Python script...'
                sh 'python3 $PYTHON_SCRIPT'
            }
        }
    }

    post {
        always {
            deleteDir()
        }
        failure {
            echo 'This will execute if the build fails'
            mail to: 'genn.veli4cko2017@yandex.ru', 
                subject: '${env.JOB_NAME} – Build # ${env.BUILD_NUMBER} failed', 
                body: '''For more information on the pipeline failure, check the console output at 
                ${env.BUILD_URL}'''
        }
    }
}
