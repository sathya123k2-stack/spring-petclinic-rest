pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sathya123k2-stack/spring-petclinic-rest.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

    }
}
