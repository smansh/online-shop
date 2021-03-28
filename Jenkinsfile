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
        sh 'docker push smansh2018/phpmysql_app'
                  
}
}
