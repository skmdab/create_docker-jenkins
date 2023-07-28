pipeline{

    agent any

    stages{
        stage('Checkout the code'){
            steps{
                git branch: 'main',  url: 'https://github.com/skmdab/create_docker_jenkins.git'
            }
        }

        stage('Creating server'){
            steps{
                sh "sh aws_create.sh"
            }
        }

        stage('Installing docker+jenkins package into server'){
            steps{
                withCredentials([file(credentialsId: 'pemfile', variable: 'PEMFILE')]) {
		sh 'ansible-playbook installdocker+jenkins.yaml --private-key="$PEMFILE"'
		}
            }
        }
    }
}
