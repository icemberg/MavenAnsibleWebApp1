pipeline {
    agent any  // Use any available agent
    


    tools {
        maven 'Maven'  // Ensure this matches the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/icemberg/MavenAnsibleWebApp1.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Run Maven build
            }
        }

     stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint:true
            }
        }
        stage('Deploy') {
            steps {
               sh 'mvn clean package'  
               sh 'ansible-playbook playbook.yml -i hosts.ini --vault-password-file .vault_pass.txt -vvv'
            }
        }

                  
    }

   }
