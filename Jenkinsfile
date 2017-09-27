pipeline {
    agent any
    stages {
        stage('Java Build') {
        	steps {
        		echo "java build"
			echo DOCKER_USER 
			echo DOCKER_PWD
			/*
			sh"""
				cd ./my-app
				mvn clean package
				java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
			"""
			*/
        	}
        }
	    
        stage('docker Build') {
		steps {
			echo "docker build"
			/*
			sh"""
				cd my-app/src/main/docker/
				cp ${WORKSPACE}/my-app/target/my-app-1.0-SNAPSHOT.jar .
				docker build -t deploymentcoe/myapp .
				docker login -u $DOCKER_USER -p $DOCKER_PWD
				docker images
				docker rmi myapp
			"""
			*/
        	}
        }

        stage('Deployment') {
			steps {
				echo "Deployment"
        	}
        }

    }
}
