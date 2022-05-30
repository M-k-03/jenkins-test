pipeline {
    agent any
    tools {
			maven "Maven"
			jdk "JDK"
		}
    stages {
        stage('Build') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo 'Building..'
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /home/ubuntu/apache-maven-3.8.5"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
