pipeline {
agent {
label 'nginxserver'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build1') 
{
    steps {
        node ('nginxserver')
       sh "cd /home/chandu ; sudo apt-get update "
       sh "cd /home/chandu ; sudo apt-get install apache2 -y "
       sh "cd /home/chandu ; sudo apt-get install nginx -y"
       sh "cd /home/chandu ; sudo systemctl start nginx"
       sh "cd /home/chandu ; sudo ufw allow 'Nginx HTTP"

    }
}
stage ('Build2')
{
    steps {
        node ('ansible')
       sh "cd /home/chandu ; sudo ansible-playbook copy.yml "
    }
}
stage ('nginxdeployment')
    { 
        steps {
            node ('nginxserver') {
           sh "cd /home/chandu ; sudo systemctl restart nginx "
    }
}
}
}
}

