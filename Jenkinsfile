pipeline {
agent {
label 'nginxserver'
}

stages {
    
stage ('Build1') 
{
    steps {
       sh "cd /home/ubuntu ; sudo apt-get update "
       sh "cd /home/ubuntu ; sudo apt-get install apache2 -y "
       sh "cd /home/ubuntu ; sudo apt-get install nginx -y"
       sh "cd /home/ubuntu ; sudo ufw allow 'Nginx HTTP"

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
           sh "cd /home/ubuntu ; sudo systemctl restart nginx "
    }
}
}
}
}

