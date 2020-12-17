pipeline {
    agent any
    stages { 
        stage ('Repositorio') {
            steps {
                echo 'Clonamos el repositorio'
                git url:'https://github.com/galamoga/ejemplowebapp'
            }
        }
        stage ('Empaquetado') {
            steps {
                echo 'Empaqueto mediante Maven'
                sh 'mvn package'
            }
        }
        stage ('Despliegue') {
            steps {
                echo 'Despliegue en tomcat'
                deploy adapters: [tomcat9(credentialsId: '762b6af4-5992-47e4-b930-0d5f3f724423', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miproy2.war'
            }
        }
    }
    post {
        always {
            echo 'Yo me ejecuto siempre'
        }
        success {
            echo 'Yo me ejecuto si acabo bien'
        }
        failure {
            echo 'Yo me ejecuto si ha ido mal'
        }
        changed {
            echo 'Yo me ejecuto si hay cambio de estado'
        }
    }
}