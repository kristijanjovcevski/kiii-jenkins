node{
  def app
  stage('Clone repository') {
  checkout scm
  }

  stage('Build image') {
  app = docker.build("kristijanjovcevski/kiii-jenkins")
  }

  stage('Push image') {
      docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
      app.push("${env.BRANCHNAME)-$(env.BUILD_NUMBER}")
      app.push("$(env.BRANCH NAME)-latest")
  }
