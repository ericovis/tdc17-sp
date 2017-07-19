pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'ansible-galaxy install -r requirements.yml -p roles --force'
            }
        }
        stage('Validate') {
            steps {
                sh 'packer validate packer.json'
                sh 'ansible-playbook playbook.yml --syntax-check'
            }
        }
        stage('Create') {
            steps {
                sh 'packer build packer.json'
            }
        }
    }
}
