pipeline {
    agent {
        docker {
            image 'dockerappbuild:latest'
			label 'Docker'
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}