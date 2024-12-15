pipeline {
    agent {
        docker {
            image 'python:3.13.1'
            args '-u root:root'
        }
    }    
    stages {
        stage('install and run tests on python 3.12') {
            steps {
                sh 'python -m venv .venv'
                sh '. .venv/bin/activate'
                sh 'pip install -r requirements.txt'
                sh 'pytest --html=report_312.html --self-contained-html'
            }
        }
        stage('install and run tests on python 3.13') {
            steps {
                docker.image('python:3.13').withRun { agent ->
                    sh 'python -m venv .venv'
                    sh '. .venv/bin/activate'
                    sh 'pip install -r requirements.txt'
                    sh 'pytest --html=report_313.html --self-contained-html'
                }
            }
        }
    }
}
