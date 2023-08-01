pipeline {
    agent {
        node {
            label "primesquare-local"
        }
    }
    
    tools {
        nodejs "Nodejs"
        sonarqubeScanner ('sonar-scanner')
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
 		stage('SonarQube Analysis') {
    			def scannerHome = tool 'sonar-scanner';
    		steps{
			withSonarQubeEnv('sonar-scanner') {
      			sh "${scannerHome}/bin/sonar-scanner"
   			 }
}
                    }
                }
            }
        
    

