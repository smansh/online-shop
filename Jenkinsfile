currentBuild.displayName = "Online-Shopping-#"+currentBuild.number

node{

    stage('SCM Checkout')
    {
        git credentialsId: 'git-creds', url: ' https://github.com/smansh/online-shop.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'sudo docker-compose build'
        sh 'sudo docker-compose up -d'
    }
  stage('PUSH image to Docker Hub')
    {
       withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) 
     {
        sh "docker login -u smansh2018 -p ${dockerHubPwd}"
     }
        sh 'docker tag sample-devops-project-online-shopping_web:latest smansh2018/sample-devops-project-online-shopping_web:latest'
        sh 'docker push smansh2018/sample-devops-project-online-shopping_web'
                  
}
}
