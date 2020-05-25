node ('master'){  
    def app
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
   
    
    stage('Build-and-Tag') {
    /* This builds the actual image; synonymous to
         * docker build on the command line */
        app = docker.build("rajcena3535/snake")
    }
    stage('Post-to-dockerhub') {
    
     docker.withRegistry('https://registry.hub.docker.com', 'training_creds') {
            app.push("latest")
        			}
         }
  
  
    
    stage('Pull-image-server') {
    
         sh "/home/jenkins/docker-jenkins/jenkins_data/tools/docker-compose down"
         sh "/home/jenkins/docker-jenkins/jenkins_data/tools/docker-compose up -d"	
      }
    
   
}
