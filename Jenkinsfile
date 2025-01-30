def gv

pipeline {
    agent any
    tools {
        maven 'Maven=3.9.9'
    }
    stages {
        stage("init") {
            steps {
                script {
                    echo "init"
                    echo "init pipeline for $BRANCH_NAME"

                    gv = load "script.groovy"

                }
            }  
        }
        stage("build jar") {
            when {
                expression {
                    BRANCH_NAME == 'main'
                }
            }
            steps {
                script {
                    echo "building jar"
                    // gv.buildJar()
                }
            }
        }
        stage("build image") {
            when {
                expression {
                    BRANCH_NAME == 'main'
                }
            }
            steps {
                script {
                    echo "building image"
                    // gv.buildImage()
                }
            }
        }
        stage("deploy") {
            when {
                expression {
                    BRANCH_NAME == 'main'
                }
            }
            steps {
                script {
                    echo "deploying"
                    // gv.deployApp()
                }
            }
        }
    }   
}
