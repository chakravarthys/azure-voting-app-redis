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
	   echo 'workspace is $WORKSPACE'
	   dir('$WORKSPACE/azure-vote'){
		script{
		docker.withRegistry('https://index.docker.io/v1/','dockercred')
		def image=docker.build('https://hub.docker.com/repository/docker/chakravarthys/dockerrepo')
		image.push()
}	
}
}
}
   }
}
