pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulls from your GitHub repo (already linked in Jenkins job config)
                checkout scm
            }
        }

        stage('Ansible Ping Test') {
            steps {
                bat '''
                echo ===== Checking Ansible inside WSL =====
                wsl ansible --version

                echo ===== Testing connectivity to hosts =====
                wsl ansible -i /mnt/c/Users/Pritha.Mohanta/OneDrive\\ -\\ Bottomline/Desktop/ansible-demo/inventory.ini all -m ping -vv
                '''
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                bat '''
                echo ===== Running Playbook =====
                wsl ansible-playbook -i /mnt/c/Users/Pritha.Mohanta/OneDrive\\ -\\ Bottomline/Desktop/ansible-demo/inventory.ini site.yml -vv
                '''
            }
        }
    }
}
