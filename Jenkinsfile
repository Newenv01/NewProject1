pipeline {
    agent any
       triggers {
        pollSCM "0 * * * *"
       }
    stages {
        stage('Build Application') { 
            steps {
                echo '=== New Test Building Petclinic Application ==='
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test Application') {
            steps {
                echo '=== Testing Petclinic Application ==='
                sh 'mvn test'
            }
        }
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                echo '=== Building Petclinic Docker Image ==='
                script {
                    echo "Testing Docker Build"
                }
            }
        }
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                echo '=== Pushing Petclinic Docker Image ==='
            }
        }
        stage('Remove local images') {
            steps {
                echo '=== DDNewDelete the local docker images ==='
            }
        }
    }
