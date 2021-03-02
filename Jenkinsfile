pipeline {
agent {
label 'ansible'
}

stages {
    
stage ('Build1')
{
    steps {
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

