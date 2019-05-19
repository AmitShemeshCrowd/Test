node {
   
   stage('Preparation') {
	  git 'https://github.com/AmitShemeshCrowd/Test.git'
   }
   stage('Build') {
	  
		sh "docker build -t test:${env.BUILD_ID} ."
		
		withCredentials([usernamePassword(credentialsId: 'DockerHUb', passwordVariable: 'dkrhb_pss', usernameVariable: 'dkrhb_usr')]) {
			sh """
			  docker login -u ${dkrhb_usr} -p ${dkrhb_pss}
			  docker tag test:${env.BUILD_ID} amitshemeshcrowd/test:${env.BUILD_ID}
			  docker tag amitshemeshcrowd/test:${env.BUILD_ID} amitshemeshcrowd/test:latest

			  docker push amitshemeshcrowd/test:${env.BUILD_ID}
			"""
		}
   }
   
}
