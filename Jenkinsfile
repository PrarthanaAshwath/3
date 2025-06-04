pipeline
{
	agent any
	tools
	{
		maven 'maven'
	}
	stages
	{
		stage('Checkout')
		{
			steps{
				git 'https://github.com/PrarthanaAshwath/3.git'
			}
		}
		stage('Build')
		{
			steps{
				sh 'mvn clean package'
			}
		}
		stage('Archive')
		{
			steps{
				acrhiveArtifacts artifacts:'target/*.war',fingerprint:true
			}
		}
		stage('Deploy')
		{
			steps{
				sh 'mvn clean package'
				ansiblePlaybook playbook:'ansible/deploy.yml',inventory:'ansible/hosts.ini'
			}
		}
	}
}
		
