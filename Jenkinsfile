pipeline {
    agent {
      node {
        label 'agent11'
      }
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/example/repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Publish Test Results') {
            steps {
                junit 'target/surefire-reports/*.xml'  // Collects test reports
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed!"
        }
        success {
            echo "Tests passed successfully!"
        }
        failure {
            echo "Tests failed!"
        }
    }
}
