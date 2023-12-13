pipeline {
    agent any
    tools {
        maven "Maven_Home"
         }
    stages {
        stage('Checkout') {
            steps{
			git branch: 'main', credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/HelloServlet.git'
                echo "Checkout Success"
            }
        }
        stage('MavenBuild') {
            steps{
			sh'mvn clean install'
                echo "Build Success"
            }
        }
        stage('Deploy') {
            steps{
		sshagent(['deploy_user']) {
		
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/CICDJOB-1/target/helloworld.war ec2-user@44.210.130.93:/opt/apache-tomcat-9.0.84/webapps"
			echo "Deploy Success"
			}	
            }
        }
    }
}
