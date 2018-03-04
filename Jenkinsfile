#!groovy

// https://github.com/feedhenry/fh-pipeline-library
@Library('fh-pipeline-library') _

println 'Hi from a trusted PR!'

node('nodejs6') {

    step([$class: 'WsCleanup'])

    stage ('Checkout') {
        checkout scm
    }

    stage('Install Dependencies') {
        npmInstall {}
    }

    stage('Lint') {
        sh 'grunt eslint'
    }

    stage('Build') {
        gruntBuild {
            name = 'grunt-fh-build'
        }
    }
}
