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
    steps
    {
       sh "cd /home/naga/node/Angular-JumpStart ; sudo apt-get update "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo apt-get install nodejs "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo npm install -g @angular/cli@11.0.0 -y"
       sh "cd /home/naga/node/Angular-JumpStart ; sudo ng build "
       sh "cd /home/naga ; sudo ansible-playbook copy.yml "
    }
}
stage ('angulardeployment')
    { 
        steps {
            node ('nginxserver') {
           sh "cd /home/naga ; sudo systemctl restart nginx "
    }
}
}
}
}
