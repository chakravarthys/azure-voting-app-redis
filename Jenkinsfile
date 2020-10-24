pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('push-container'){
	steps{ 
	   echo "workspace is ${env.WORKSPACE}"
	   dir("${env.WORKSPACE}/azure-vote"){
		script{
			docker.withRegistry('https://index.docker.io/v1/','dockercred'){
			def image=docker.build('chakravarthys/dockerrepo:latest')
			image.push()
}
}	
}
}
}
	stage('trivy scan'){
	steps{
		sh 'trivy chakravarthys/dockerrepo'
}
	}
   }
}
