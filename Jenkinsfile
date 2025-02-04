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


                    //gv = load "script.groovy"


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
            /*when {
                expression {
                    BRANCH_NAME == 'main'
                }
            }*/
            steps {
                script {
                    echo "deploying"

                    def dockerCmd = 'docker run -p 3080:3080 -d danbutuc/demo-app:1.0'
                    sshagent(['ec2-private-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@34.244.129.21 ${dockerCmd}"
                    }

                    // gv.deployApp()
                }
            }
        }
    }   
}
