pipeline{
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
                    def customImage = docker.build("my-image:${env.BUILD_ID}")
                    customImage.push()
                }
                 }
             }
    
         }
    
    
    
}
