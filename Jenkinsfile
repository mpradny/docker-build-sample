pipeline {
    agent {
        docker {
            image 'registry.pris.to/docker/domino-appbuild:V1200_02112021prod'
			label 'Docker'
			args '-v jenkins-m2-repo:/local/notes/.m2/repository'
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
		
		stage('Publish') { 
            steps {
                archiveArtifacts artifacts: 'target/*.nsf', fingerprint: true
            }
        }
    }
}