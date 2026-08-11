pipeline {
    agent any 

tools {
    maven 'Maven-3.9.11'
    jdk 'JDK-21'
}
    stages {

        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t spring-petclinic:v1 .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag spring-petclinic:v1 sathya123k2/spring-petclinic:v1'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push sathya123k2/spring-petclinic:v1'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f spring-petclinic || true
                docker run -d --name spring-petclinic -p 9966:9966 sathya123k2/spring-petclinic:v1
                '''
            }
        }
    }
}
