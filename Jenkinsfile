pipeline {
  agent {
        node{
                label "Frontend"
}
}
  tools {
nodejs "Nodejs"
}

  stages {

//    stage('Git') {
//      steps {
//        git 'https://github.com/****/****'
//      }
//    }

    stage('Build') {
      steps {
                node('Nodejs'){
                sh 'npm install'
         sh 'npm build'
                }
			}
		}
	}
}
