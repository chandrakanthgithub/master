pipeline {
agent {
label 'Ansible'
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
       sh "cd /home/chandu ; sudo apt-get install nginx"
       sh "cd /home/chandu ; sudo systemctl start nginx"
       sh "cd /home/chandu ; sudo ufw allow 'Nginx HTTP"

    }
}
stage ('Build2')
{
    steps {
        node ('Ansible')
       sh "cd /home/chandu ; sudo ansible-playbook copy.yml "
    }
}
stage ('nginxdeployment')
    { 
        steps {
            node ('nginxserver') {
           sh "cd /home/naga ; sudo systemctl restart nginx "
    }
}
}
}
}
