pipeline { 
    agent any 
    environment {
        DOCKER_IMAGE = 'Dockerfile' // Название вашего Docker-образа
    }
    tools {
  'org.jenkinsci.plugins.docker.commons.tools.DockerTool' 'docker'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Сборка приложения...'
                sh 'docker build . -t $DOCKER_IMAGE'
            }
        }

        stage('Test') {
            steps {
                echo 'Тестирование приложения...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Развёртывание приложения...'
                sh 'docker run -d --name $DOCKER_IMAGE -p 8080:80 $DOCKER_IMAGE'
            }
        }
    }

    post{
        always{
            deleteDir()
        }
        failure{
            echo 'Это будет выполняться, если задача провалилась' 
            mail to: 'genn.veli4cko2017@yandex.ru', 
                subject: '${env.JOB_NAME} – Сборка № ${env.BUILD_NUMBER} провалилась', 
                body: '''Для получения дополнительной информации о провале пайплайна, проверьте консольный вывод по 
                адресу ${env.BUILD_URL}'''
        } 
        }
}
