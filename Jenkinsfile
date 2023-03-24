pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-image-cren')
	}

    stages {
        
        stage('clone src') {
            steps {
                git branch: 'master', url: 'https://github.com/hackcoderr/nginx.git'
            }
        }
        stage('build docker image') {
            steps {
                sh 'docker build -t react-simple-app .'
                sh 'docker tag react-simple-app vaibhav099/react-simple-app:latest'
            }
        }
        stage('push docker image') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push vaibhav099/react-simple-app:latest'
            }
       }

    }       
}
