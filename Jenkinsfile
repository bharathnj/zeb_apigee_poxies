pipeline {
    agent {
    	label 'docker-mule'
    }
    stages {
      	stage('Checkout') {
            steps {
            	checkout scm
            }
        }
        stage ('Build') {
            steps {
                echo 'Building application...'
              	// build archive with server
              	archiveArtifacts(artifacts: 'target/*.zip', onlyIfSuccessful: true, fingerprint: true)
            }
        }
      	stage('Deploy') {
            steps {
                echo 'Deploying application...'
              	sh 'mvn -Dmaven.repo.local="~/.m2/repository" package mule:deploy'
            }
        }
    }
}

