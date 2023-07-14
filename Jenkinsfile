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
                sh 'npm i @angular/cdk@10.2.5 @angular/forms@10.2.5'
		sh 'npm run build'
                }
	    }
	}
}
