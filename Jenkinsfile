pipeline {
    agent {
        docker {
            args '-u root:root'
        }
    }
    stages {
        parallel {
                stage('install and run tests on python 3.12') {
                    agent {
                        docker { image 'python:3.12' }
                    }
                    steps {
                        script {
                            sh 'python3.12 -m venv12 .venv'
                            sh '. .venv/bin/activate'
                            sh 'pip install -r requirements.txt'
                            sh 'pytest --html=report_313.html --self-contained-html'
                        }
                    }
                }
            stage('install and run tests on python 3.13') {
                agent {
                    docker { image 'python:3.13' }
                }
                steps {
                    script {

                        sh 'python3.13 -m venv13 .venv'
                        sh '. .venv/bin/activate'
                        sh 'pip install -r requirements.txt'
                        sh 'pytest --html=report_313.html --self-contained-html'
                    }
                }
            }
        }
    }
}