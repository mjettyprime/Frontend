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
//        stage('Git') {
//            steps {
//                git 'https://github.com/****/****'
//            }
//        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
	stage('crediantials'){
	    steps {
                script {
                    def sudoPassword = input(
                        id: 'sudo-password',
                        message: 'Enter sudo password:',
                        parameters: [
                            [$class: 'PasswordParameterDefinition', defaultValue: '', description: 'Sudo password', name: 'SUDO_PASSWORD']
                        ]
                    ).toString()

                    sh '''
                        echo "$sudoPassword" | sudo -S /opt/Sonar-scanner/bin/sonar-scanner -Dsonar.projectName=test2 -Dsonar.projectKey=test2
                        echo "$sudoPassword" 
                    '''
                }
            }
		}
        stage('Sonar') {
            steps {
                script {
                    withSonarQubeEnv(redentialsId: 'sonar') {
                        sh "sudo -S ${SUDO_PASSWORD} /opt/Sonar-scanner/bin/sonar-scanner -Dsonar.projectName=test2 -Dsonar.projectKey=test2"
                    }
                }
            }
        }
    }
}
