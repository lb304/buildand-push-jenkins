node {

   def registryProjet='web/'
   def IMAGE="${registryProjet}app:3.5"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 8000:80") { c ->
       
          }
    }

    stage('Push') {
          docker.withRegistry('https://hub.docker.com/', 'hub_docker_id') {
              img.push 'latest'
              img.push()
          }
    }

}

