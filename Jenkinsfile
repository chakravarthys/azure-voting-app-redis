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
	   echo 'workspace is ${env.WORKSPACE}'
	   dir('${env.WORKSPACE}/azure-vote'){
		script{
			docker.withRegistry('https://index.docker.io/v1/','dockercred'){
			def image=docker.build('myimage:1.0')
			image.push()
}
}	
}
}
}
   }
}
