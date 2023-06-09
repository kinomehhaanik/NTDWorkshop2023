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
    stage ('Run API container') {
        steps {
            sh 'docker run -p 3000:3000 --network bridge --name api-container --rm -d marko/movie-api'
        }
    }
    stage('Build Test container') {
        steps {
            sh 'docker build tests -t <YOUR_USER>/movie-api-tests'
        }
    }
    stage('Execute tests') {
        steps {
            sh 'docker run -e PORT=3000 -e BASE_URI=172.17.0.2 --network bridge --rm <YOUR_USER>/movie-api-tests'
        }
    }
    stage('Cleanup') {
        steps {
            sh 'docker kill api-container'
        }
    }
}
