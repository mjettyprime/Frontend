pipeline {
  agent {
        node{
                label "Frontend"
}
}
  tools {
nodejs "node"
}

  stages {

//    stage('Git') {
//      steps {
//        git 'https://github.com/****/****'
//      }
//    }

    stage('Build') {
      steps {
		node('Node.js 14'){
		sh 'npm install'
         sh 'npm build'
		} 
      }
    }


