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

        stage('Sonar') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonar') {
 			def scannerHome = tool 'SonarScanner'
                        sh "${scannerHome}/bin/sonar-scanner"                    }
                }
            }
        }
    }
}
