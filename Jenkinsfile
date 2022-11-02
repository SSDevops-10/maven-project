pipeline {
	agent any 
	stages {
		  stage ('clean')
                {
                        steps {
                        sh 'mvn clean'
                        }
                }

		stage ('SCM initialize')
		{
			steps {
			git 'https://github.com/SSDevops-10/demoappjenkins.git'
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
