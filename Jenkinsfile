pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'Dockerfile'  // Docker image name
    }
    stages {
        stage('Initialize') {
            steps {
                echo 'Initializing environment...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'docker build . -t $DOCKER_IMAGE'
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
                sh 'docker run -d --name $DOCKER_IMAGE -p 8080:80 $DOCKER_IMAGE'
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
