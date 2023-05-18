// Declarative Pipeline
pipeline{
    // agent {label 'python'}
    agent any
    environment{
        MY_VERSION_VAR = "1.0.0"
    }
    stages{
        stage("init"){
            steps{
                echo "init"
            }
        }
        stage("build dev"){
            // options{
            //     ansiColor("xterm")
            // }
            when{
                branch "development"
            }
            steps{
                echo "build your nice project with version ${MY_VERSION_VAR}"
            }
        }
        stage("build master"){
            when{
                branch "master"
            }
            steps{
                echo "build your nice project!"
            }
        }
        stage("accept deployment"){
            options{
                timeout(time: 2, unit: "MINUTES")
            }
            steps{
                input(message: "Approve deploy?", ok:"Yes")
            }
        }
        stage("push"){
            // agent{
            //     docker { image 'sebasnaa/azagent:1.0' }
            // }
            steps{
                echo "build your nice project!"
            }
        }
    }
    post {
        success {
            sh 'python3 --version'
            sh 'python3 helloworld.py'
            // sh './helloworld.py'
        }
    }
}