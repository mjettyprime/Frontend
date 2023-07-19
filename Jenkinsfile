pipeline {
    agent {
        node {
            label "primesquare-local"
        }
    }
    
    tools {
        nodejs "Nodejs"
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Credentials') {
            steps {
                script {
                    def sudoPassword = input(
                        id: 'sudo-password',
                        message: 'Enter sudo password:',
                        parameters: [
                            password(name: 'SUDO_PASSWORD', defaultValue: '', description: 'Sudo password')
                        ]
                    )
                    sh "echo '$sudoPassword'"
                }
            }
        }
        
        stage('Sonar') {
            steps {
                withSonarQubeEnv(credentialsId: 'sonar') {
                    script {
                        sh "sudo -S ${env.SUDO_PASSWORD} /opt/Sonar-scanner/bin/sonar-scanner -Dsonar.projectName=test2 -Dsonar.projectKey=test2"
                    }
                }
            }
        }
    }
}
