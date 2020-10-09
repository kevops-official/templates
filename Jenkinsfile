// Demo Jenkinsfile

GIT_URL          = "https://github.com/kevops-official/templates.git"
GIT_BRANCH       = "master"
DOCKER_CONTAINER = "demo-web-template"
DOCKER_IMAGE     = "web-template"

pipeline{
    agent{
        label "docker-demo"
    }
    stages{
        stage("Get code"){
            steps{
                git url: "${GIT_URL}", branch: "${GIT_BRANCH}"
            }
        }
        stage("Create Docker Image"){
            steps{
                dir("docker"){
                    sh"""#!/bin/bash
                    docker build -t ${DOCKER_IMAGE} .
                    """
                }
            }
        }
        stage("Deploy new contianer"){
            steps{
                sh"""#!/bin/bash
                docker rm -f ${DOCKER_CONTAINER}
                docker run -itd --name ${DOCKER_CONTAINER} -p 8888:80 ${DOCKER_IMAGE}
                """
            }
        }
    }
}