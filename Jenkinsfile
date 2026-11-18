pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Получение исходного кода из GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Сборка приложения...'
                sh '''
                    echo "Building application..."
                    echo "Build completed successfully" > build.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Тестирование приложения...'
                sh '''
                    test -f app.txt
                    test -f build.txt
                    echo "All tests passed"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Развёртывание приложения...'
                sh '''
                    mkdir -p deployment
                    cp app.txt deployment/
                    cp build.txt deployment/
                    echo "Application deployed successfully"
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline успешно выполнен.'
        }

        failure {
            echo 'Pipeline завершился с ошибкой.'
        }

        always {
            echo 'Работа Pipeline завершена.'
        }
    }
}
