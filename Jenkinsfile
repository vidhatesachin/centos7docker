node{
	stage ('Scm Checkout'){
	git credentialsId: 'github', url: 'https://github.com/anoopgawande/centos7docker.git'}
	
	stage ('Build Docker Image'){
	sh '/usr/bin/docker build -t agawande/httpd:$BUILD_NUMBER .'}
	
	stage ('Push Docker Image'){
	withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerpwd', usernameVariable: 'dockeruser')]) {
    sh "/usr/bin/docker login -u $dockeruser -p $dockerpwd}"
	sh '/usr/bin/docker push agawande/httpd:$BUILD_NUMBER'}
