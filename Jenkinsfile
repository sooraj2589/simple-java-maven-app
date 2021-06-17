pipeline {
    agent {
        docker {
            image 'maven:3.5.4-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }  
        }
         stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Upload to Artifactory') {
            steps {
                sh 'echo upload to artifactory'
            }
        }
        
       /* stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }*/
    }
}
