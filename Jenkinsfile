node {
     def app
     
  stages {        
    stage('git_clone') {
      steps {
        git 'https://github.com/rsreddy281/jenkis_docker.git'
      }
    }      
  
  stage('Build image') {
    app = docker.build("249121/nodeapp")
  }
  
  stage('Test image') {
    app.inside {
      echo "Tests Passed"
    }
  }
  
  stage('Push image') {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
      echo "Trying to push Docker Build to DockerHub"
  }
}
