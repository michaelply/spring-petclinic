pipeline {
    agent any
    stages {
      stage("Execute Ansible") {
        agent any
            // steps {
            //     ansiblePlaybook installation: 'Ansible', inventory: 'dev.inv', playbook: 'test_playbook.yml'
            // } 
            steps {
                sh 'ansible-playbook playbook.yml'
            } 
        post {
            success {
                sh 'echo "success"'
            }
        }
      }
    }
}