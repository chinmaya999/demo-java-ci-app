pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning the repository...'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                pkill -f jenkins-java-app-1.0.0.jar || true
                nohup java -jar target/jenkins-java-app-1.0.0.jar > app.log 2>&1 &
                '''
            }
        }
    }
}

