pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout to original repo'
                git 'https://github.com/Harshpatil7770/SpringBoot-UnitTesting.git'
            }
        }

        stage('Build & Test') {
            steps {
                sh '''
                echo "Building Jar and running all the test cases"
                mvn clean package -DskipTests=true
                echo "Build finished"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to dev server'
                sh '''
                scp target/og.jar ec2-user@98.82.20.70:/app/lib
                ssh ec2-user@98.82.20.70 'nohup /app/start.sh &'
                '''
                echo 'Deployed Successfully'
            }
        }
    }
}
