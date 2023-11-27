pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80282/exam.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_qoge6wgIk0ZER9upIo4ZhaOD0zg | /usr/bin/docker login -u heenashinganjude --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t heenashinganjude/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push heenashinganjude/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9876:80 --replicas 5 heenashinganjude/mywebsite'
            }
        }
    }
}
