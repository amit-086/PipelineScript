pipeline {
    agent any

    stages {
        stage('Git-Checkout') {
            steps {
                echo 'checking out from git-repo';
                git 'https://github.com/amit-086/PipelineScript.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project!';
                bat 'mvn package'
            }
        }    
        stage('Deploy') {
            steps {
                echo 'Deploying to tomcat server';
                deploy adapters: [tomcat8(credentialsId: 'd65a214e-cf17-4a75-b14d-ae88c8022a9d', path: '', url: 'http://localhost:8082/')], contextPath: 'Web_App', onFailure: false, war: '**/*.war'
            }
        }
    }
    post {
        success {
            echo "successful!";
        }
        failure {
            echo "unsuccessful!";
        }
        unstable {
            echo "unstable!";
        }
        changed {
            echo "state of pipeline is changed!";
        }
    }
}
