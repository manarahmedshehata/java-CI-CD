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
			
			withCredentials([usernamePassword(credentialsId: '18b57317-0966-4f4a-9fa8-49f733bc09bd', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
				sh """
				cd my-app/src/main/docker/
				cp ${WORKSPACE}/my-app/target/my-app-1.0-SNAPSHOT.jar .
				docker build -t deploymentcoe/myapp .
				docker login --username $USERNAME --password $PASSWORD
				docker push deploymentcoe/myapp
				docker images
				#docker rmi myapp
				cd ${WORKSPACE}/
				"""
				//deleteDir()
			}
			
			
        	}
        }

        stage('Deployment') {
			steps {
				echo "Deployment"
				sh """
					kubectl delete -f ./manifests/deployment.yaml
					kubectl apply -f ./manifests
				"""
        	}
        }

    }
}
