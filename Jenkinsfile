pipeline {
    agent {
        node {
            label 'Jenkins-Slave-Node'  
        }
    }
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("Build Code") { 
            steps {
                echo "Build started"
                sh 'mvn clean package -Dmaven.test.skip=true'
                
            }
        }
    }
}

stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-scanner-meportal'
            }
            steps{
                withSonarQubeEnv('sonar-server-meportal') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }