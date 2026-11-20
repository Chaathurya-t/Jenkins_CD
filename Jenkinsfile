
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Java Application'
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying JAR'

                bat '''
                if not exist "C:\\JenkinsDeploy\\MultiplicationTable" mkdir "C:\\JenkinsDeploy\\MultiplicationTable"

                copy /Y "target\\multiplication-table-1.0.jar" "C:\\JenkinsDeploy\\MultiplicationTable\\multiplication-table.jar"
                '''
            }
        }

        stage('Execute') {
            steps {
                echo 'Executing Deployed Application'

                bat '''
                echo 5 | java -jar "C:\\JenkinsDeploy\\MultiplicationTable\\multiplication-table.jar"
                '''
            }
        }
    }

    post {
        success {
            echo 'CD Pipeline Executed Successfully'
        }
        failure {
            echo 'CD Pipeline Failed'
        }
    }
}
