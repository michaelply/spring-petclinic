pipeline {
    agent any
    options {
        copyArtifactPermission('spring-petclinic');
    }
    stages {
      stage("Maven Build") {
        agent any
            steps {
                sh './mvnw clean package'
            } 
        post {
            success {
                archiveArtifacts 'target/*.jar'
            }
        }
      }

      stage("Copy Artifact") {
            steps {
                script {
                    step ([$class: 'CopyArtifact',
                        projectName: 'spring-petclinic',
                        filter: "target/*.jar",
                        target: 'artifact']);
                }
            } 
      }

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