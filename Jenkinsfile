pipeline {
  agent {
        node{
                label "primesquare-local"
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
                sh 'npm install'
                sh 'npm run build'
                }
	    }
	}
}
