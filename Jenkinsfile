// https://github.com/feedhenry/fh-pipeline-library
@Library('fh-pipeline-library') _

pipeline {

    agent {
        node {
            label 'nodejs6'
        }
    }

    stages {
        stage('Trust') {
            steps {
                enforceTrustedApproval()
            }
        }

        stage('Checkout') {
            steps {
                cleanWs()
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                npmInstall {}
            }
        }

        stage('Lint') {
            steps {
                sh 'grunt eslint'
            }
        }

        stage('Build') {
            steps {
                script {
                    gruntBuild {
                        name = 'grunt-fh-build'
                    }
                }
            }
        }
    }
}
