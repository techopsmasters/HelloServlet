pipeline {
    agent any
       tools {
        maven "maven"
    }
    stages {
        stage('Code Checkout') {
            steps {
            git branch: 'main', credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/HelloServlet.git'
            
                echo 'Code checkout done sucessfully.'
            }
			}
            stage('Code Build') {
            steps {
            sh 'mvn clean package'
            echo 'Code Build done sucessfully.'
            }
            }
        stage('CodeDeploy') {
        steps {
           sshagent(['deploy_user']) {
               
               sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Job-5/target/helloworld.war  ec2-user@3.16.216.210:/opt/apache-tomcat-9.0.85/webapps"
                            }         
            }
        }
    }
}
