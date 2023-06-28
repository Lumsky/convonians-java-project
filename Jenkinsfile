pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcatpassword', path: '', url: 'http://54.145.181.224:8080/')], contextPath: 'myapp', war: '**/*.war'
            }
        }
    }
}
