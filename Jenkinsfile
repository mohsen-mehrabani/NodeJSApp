pipeline {
   agent {
    docker {
        image 'mehrabani/multi-server'
        label 'latest'
        registryUrl 'https://hub.docker.com/repository/docker/mehrabani/multi-server'
        registryCredentialsId 'dockerhub'
    }
   
    stages {
      stage('Build') {
        steps {
            sh 'mvn -B'
        }
      }
    }
  }
}