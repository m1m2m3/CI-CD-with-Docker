pipeline{
    def customImage
    agent any
    stages{
       stage('SCM checkout')
            {
            steps{ 
                git 'https://github.com/m1m2m3/CI-CD-with-Docker.git'
                 }
             }
        stage('Build image')
            {
            steps{ 
                script {
                    customImage = docker.build("my-image:${env.BUILD_ID}")
                   
                }
                 }
             }
        stage('Push to Registry')
            {
            steps{ 
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://hub.docker.com/') 
                        {
                            customImage.push("${env.BUILD_ID}")
                            customImage.push("latest")
                          // some block
                        }
                echo "Trying to Push Docker Build to DockerHub"
                 }
             }
    
         }
    
    
    
}
