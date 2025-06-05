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
				archiveArtifacts artifacts: 'target/*.war',fingerprint:true
			}
		}
		stage('Deploy')
		{
			steps{
				sh 'ansiblePlaybook playbook: 'Ansible/deploy.yml',inventory:'Ansible/hosts.ini''
			}
		}
	}
}
		
