pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
		stage('Notify slack') {
			steps {
				echo "###### Running ${env.BUILD_ID} on ${env.JENKINS_URL} #####"
			}
        }
		
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
		
		stage('Test') {
            steps {
				echo "#### Test step ####"
                sh 'mvn test'
            }
            post {
                always {
                  junit 'target/surefire-reports/*.xml'
                }
            }
        }
 
		stage('Deliver') {
            steps {
				echo "#### Deliver step ####"
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
