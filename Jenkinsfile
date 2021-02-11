pipeline {
    agent {
        docker {
            image 'registry.pris.to/docker/domino-appbuild:11.0.1FP2'
			label 'Docker'
			args '-v jenkins-m2-repo:/home/notes/.m2/repository'
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