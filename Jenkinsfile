pipeline {
    agent any
    stages {
        stage('Java Build') {
        	steps {
        		echo "java build"
			sh"""
				cd ./my-app
				mvn clean package
				java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
			"""
        	}
        }
        stage('docker Build') {
			steps {
				echo "docker build"
        	}
        }
        stage('Deployment') {
			steps {
				echo "Deployment"
        	}
        }

    }
}
