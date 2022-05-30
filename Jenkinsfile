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
                echo "M2_HOME = /home/ubuntu/apache-maven-3.8.5"
            }
        }
        stage('Build') {
            steps {
                echo 'Testing..'
		 dir("/var/lib/jenkins/workspace/pipeline-test") {
		   sh 'mvn -B -DskipTests clean package'
		}
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
		deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.7.46.50:8084')], contextPath: '/demo', onFailure: false, war: 'webapp/target/*.war' 
            }
        }
    }
}
