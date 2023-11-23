pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/c2-80462/myapp.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_G4fengsiRshmqYusnlclCbcUZ7I | /usr/bin/docker login -u rajatkokane --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t rajatkokane/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker push rajatkokane/mywebsite'
            }
        }
        stage ('docker image remove') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 rajatkokane/mywebsite'
            }
        }
    }
}
