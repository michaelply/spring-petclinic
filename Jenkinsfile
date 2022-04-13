pipeline {
    agent any
    stages {
      stage("Execute Ansible") {
        agent any
            // steps {
            //     ansiblePlaybook installation: 'Ansible', inventory: 'dev.inv', playbook: 'test_playbook.yml'
            // } 
            steps {
                sh 'ansiblePlaybook test_playbook.yml'
            } 
        post {
            success {
                archiveArtifacts 'target/*.jar'
            }
        }
      }
    }
}