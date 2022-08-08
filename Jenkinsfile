pipeline {
    agent any
    stages {
        stage("Git Checkout"){
            steps{
                checkout([$class: 'GitSCM', abranches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/krishna2812/hello-world-java.git']]])
            }
        }
        stage("Build With Maven"){
            steps{
                sh 'mvn clean install'
            }
        }
        stage("Deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://3.91.8.95:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
    
}
