pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/jynx0405/MyMavenWebApp01.git'
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify WAR') {
            steps {
                sh 'ls target'
            }
        }

        stage('Run Web App (Jetty)') {
            steps {
                sh 'nohup mvn jetty:run > jetty.log 2>&1 &'
            }
        }
    }

    post {
        success {
            echo 'Web app deployed successfully on Jetty!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
