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
				echo 'Hello'
			}
        }
		
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
 
		stage('Deliver') {
			steps {
				echo 'Deliver'
			}
        }
    }
}
