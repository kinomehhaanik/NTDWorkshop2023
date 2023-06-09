pipeline {
    agent any
    stages {
        stage('My First Stage') {
            steps {
                sh 'echo Tere!'
            }
        }
	stage('Build API Container') {
	    steps {
                sh 'docker build . -t marko/movie-api'
           }

        }
    }
}
