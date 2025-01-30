def gv

pipeline {
    agent any
    tool {
        maven 'Maven=3.9.9'
    }
    stages {
        stage("init") {
            steps {
                script {
                    echo "init"
                    gv = load "script.groovy"
            
            }
        }
        stage("build jar") {
            steps {
                script {
                    echo "building jar"
                    gv.buildJar()
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building image"
                    gv.buildImage()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    gv.deployApp()
                }
            }
        }
    }   
}
