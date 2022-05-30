pipeline {
	agent any
		tools {
			maven "MAVEN"
			jdk "JDK"
		}
	stages {
		stage('Initialize'){
			steps{
				echo "PATH = ${M2_HOME}/bin:${PATH}"
				echo "M2_HOME = /home/ubuntu/apache-maven-3.8.5/bin"
			}
		}
		stage('Build') {
			steps {
					dir("/var/lib/jenkins/workspace/pipeline-test/jenkins-test") {
					sh 'mvn -B -DskipTests clean package'
				}
			}
		}
	}
	post {
		always {
			junit(
			allowEmptyResults: true,
			testResults: '*/test-reports/.xml'
			)
		}
	}
}
