pipeline{
        agent any
        stages{
                stage('---clean---'){
                        steps{
				sh "pwd"
				sh "ls"
                                sh "mvn clean -f /var/lib/jenkins/workspace/pipelineJob/Java"
                        }
                }
                stage('--test--'){
                        steps{
                                sh "mvn test"
                        }
                }
                stage('--package--'){
                        steps{
                                sh "mvn package"
                        }
                }
		stage('--sonar--'){
                        steps{
                                sh "mvn sonar:sonar"
                        }
                }
		stage('--verify--'){
                        steps{
                                sh "mvn verify"
                        }
                }
		stage('--surefire--'){
                        steps{
                                sh "mvn surefire-report:report"
				sh "mvn site"
                        }
                }
		stage('--deploy--'){
                        steps{
                                sh "cd /"
				sh "pwd"
				sh "sudo cp /var/lib/jenkins/workspace/YogaProject/Java/target/Yoga.war /home/ayshamarty/wildfly-10.1.0.Final/standalone/deployments/"
                        }
                }
        }
}