pipeline {
    environment {
    BUILD_SCRIPTS='tomcat04'
    BUILD_HOME='/var/lib/jenkins/workspace'
    }
    agent none
    stages {
        stage ('Build') {
            agent any
            steps {
                echo 'Build stage, '
               sh '''#!/bin/bash
                  sudo yum install ansible git -y &
                   wait;
                   git clone https://github.com/madhavigawari01/amolmaven1.git &
                   wait;
                   echo "Build completed successfully"
               '''
            }
        }
        stage ('Deploy') {
            agent any
            steps {
                echo 'Deploy stage, '
              sh '''#!/bin/bash
                   cd $BUILD_HOME/$BUILD_SCRIPTS
                   cd sample-tomcat-deploy/ansible-tomcat-deploy
                   ansible-playbook app-deploy.yml 
               '''    
                }
        }
        stage ('Test') {
            agent any
            steps {
                echo 'Test stage, '
            }
        }
        stage ('Teardown') {
            agent any
            steps {
                echo 'Teardown stage, '
            }
        }
    }
}
