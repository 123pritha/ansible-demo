pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                bat '''
                REM Convert Jenkins workspace path to WSL path
                for /f "delims=" %%i in ('wsl wslpath "%WORKSPACE%"') do set WSL_WS=%%i

                REM Run Ansible inside WSL
                wsl sh -lc "cd $WSL_WS/ansible && ansible-playbook -i inventory.ini site.yml -vv"
                '''
            }
        }
    }
}
