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
                    def dockerComposeCmd = "docker-compose -f docker-compose.yaml up --detach"

                    sshagent(['ec2-private-key']) {
                    sh "scp docker-compose.yaml ec2-user@34.244.129.21:/home/ec2-user"
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@34.244.129.21 ${dockerComposeCmd}"
                                        }
                    // gv.deployApp()
                }
            }
        }
    }   
}
