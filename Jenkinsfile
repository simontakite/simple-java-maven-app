pipeline {

    agent any

    stages {
        stage('dir') {
            steps {
                sh 'ls -la'
            }
        }
        stage('ansible') {
            steps {
                sh 'ansible --version'
            }
        }
        stage('inventory') {
            steps {
                //sh 'ansible -m ping webservers -i .ansible/inventory.ini --private-key /var/lib/jenkins/ansible.key -u vagrant'
                sh 'ansible-playbook .ansible/00-install-apigateway.yml -i .ansible/inventory.ini --private-key /var/lib/jenkins/ansible.key -u vagrant'
            }
        }
    }
}
