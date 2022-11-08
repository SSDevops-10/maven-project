pipeline {
	agent any

 triggers {

         pollSCM('* * * * *')
     }
	stages {

		  stage ('clean')
                {
                        steps {
                           sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean'
                        }
                }

		stage ('validate')
		{
			steps {
			sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean validate'
			}
		}
		stage ('compile')
		{
			steps {
			sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean compile'
			}
		}
		stage ('test')
		{
			steps {
			sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean test'
			}

			                               post {
                                        success {
                                                        echo 'Now Archiving...'

                }
            }
		}
		stage ('package')
		{
			steps {
			sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean package'
			}
			       post {
                                        success {
                                                        echo 'Now Archiving...'
                                                        
                }
            }

		}
		stage ('verify')
		{
			steps {
			sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean verify'
			}
		}


		stage ('Adding project to SonarQube')
		{
			steps {
			sh 'mvn sonar:sonar \
  -Dsonar.projectKey=Pipeline_Application_Pipeline \
  -Dsonar.host.url=http://54.162.108.196:9000 \
  -Dsonar.login=26a0fec56b01cd6628d5704732103cef08ffa46a'
  	}
	}
	        stage ('install')
                {
                        steps {
                        sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean verify'
                        }
				post {
                			success {
                    					echo 'Now Archiving...'
                    					archiveArtifacts artifacts: '**/target/*.war'
                }
            }
                }

		stage ('deploy')
		{
		steps {
		sshagent(['deploy_user']) 
		{
			sh 'scp -i /home/ec2-user/keynew.pem -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Application-Pipeline/webapp/target/webapp.war ec2-user@54.147.170.90:/home/ec2-user/apache-tomcat-9.0.68/webapps/'


		}
		


		}	



	}

}
}
