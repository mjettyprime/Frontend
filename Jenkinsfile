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
                            [$class: 'PasswordParameterDefinition', description: 'Sudo password', name: 'SUDO_PASSWORD']
                        ]
                    ).toString()

                     sh 'echo "$sudoPassword"'
                }
            }
		}
        stage('Sonar') {
            steps {
                script {
			withSonarQubeEnv(credentialsId: 'sonar'){
      				sh" ${SCANNER_HOME**}**}/bin/sonar-scanner \
      				-Dsonar.projectKey=test2 \
      				-Dsonar.projectName=test2 \
	  			-Dsonar.sources=. "
                    }
                }
            }
        }
    }
}
