pipeline {
	agent any 
	stages {
		  stage ('clean')
                {
                        steps {
                           sh '/opt/maven/apache-maven-3.8.6/bin/mvn clean package'
                        }
                }

		stage ('SCM initialize')
		{
			steps {
			echo "Step 1"
			}
		}
		stage ('Maven validate')
		{
			steps {
			echo "Maven validate"
			}
		}
		stage ('Maven compile')
		{
			steps {
			echo "Maven compile"
			}
		}
		stage ('Maven test')
		{
			steps {
			echo "Maven test"
			}
		}
		stage ('Maven verify')
		{
			steps {
			echo "Maven verify"
			}
		}
	}
}
