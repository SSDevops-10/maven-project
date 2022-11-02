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


	}

}
