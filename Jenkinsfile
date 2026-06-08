pipeline {
    agent any
    tools {
        jdk 'jdk21'
        maven 'maven3'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jaiswaladi246/Ekart.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test -DskipTests=true'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                SCANNER_HOME = tool 'sonar-scanner'
            }
            steps {
                withSonarQubeEnv('sonar') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner \
                    -Dsonar.projectName=Ekart \
                    -Dsonar.projectKey=Ekart \
                    -Dsonar.java.binaries=.'''
                }
            }
        }
        stage('OWASP Scan') {
            steps {
                dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'DP'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests=true'
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh 'docker build -t ekart -f docker/Dockerfile .'
                        sh 'docker tag ekart YOUR_DOCKERHUB_USERNAME/ekart:latest'
                        sh 'docker push YOUR_DOCKERHUB_USERNAME/ekart:latest'
                    }
                }
            }
        }
        stage('Trigger CD Pipeline') {
            steps {
                build job: 'CD-Pipeline', wait: true
            }
        }
    }
}
