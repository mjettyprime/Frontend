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
                    withSonarQubeEnv(redentialsId: 'sonar') {
                        sh "sudo -S /opt/Sonar-scanner/bin/sonar-scanner -Dsonar.projectName=test2 -Dsonar.projectKey=test2"
                    }
                }
            }
        }
    }
}
