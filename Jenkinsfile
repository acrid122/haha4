pipeline {
    agent any
    stages {
        stage('Initialize') {
            steps {
                echo 'Initializing environment...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the application...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
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
