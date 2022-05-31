pipeline {
    agent any
    tools {
			maven "Maven"
			jdk "JDK"
		}
    stages {
        stage('Initializing') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo 'Building..'
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /usr/share/apache-maven"
            }
        }
        stage('Build') {
            steps {
                echo 'Testing..'
		 dir("/var/lib/jenkins/workspace/jenkins-build-test") {
		   sh 'mvn -B -DskipTests clean package'
		}
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
		deploy adapters: [tomcat9(credentialsId: 'tomcat', url: 'http://13.127.100.11:8082')], contextPath: '/demo', onFailure: false, war: 'jenkins-build-test/target/*.war' 
            }
        }
    }
}
