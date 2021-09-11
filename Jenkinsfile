node {
  def dockerImage
   stage('Clone Repo') { // for display purposes
	      git 'https://github.com/codeboyatwork/dockerfiledemo.git'
	    } 
  stage('Build Docker Image') {
	      // build docker image
	      dockerImage = docker.build("ultra-resolver-320013/myapp:${env.BUILD_NUMBER}")
	    }
  stage('Deploy Docker Image') {
		    docker.withRegistry('https://gcr.io', 'gcr:ultra-resolver-320013-cloud-run') {
		    dockerImage.push("${env.BUILD_NUMBER}")
		    dockerImage.push("latest")
		    }
	    }
}
