pipeline{
    agent any
    stages{
        stage('GIT') {
            agent {
                label 'gcc'
            }
  steps {
    git branch: 'main', credentialsId: 'git', url: 'https://github.com/nmanojkoli1997/devopsclass.git'
            sh '''
            #!/bin/bash
cd /home/ubuntu/workspace/ctest/
make
mkdir -p target
cp -r /home/ubuntu/workspace/ctest/*.exe target/
echo "${NODE_LABELS}"
            '''
         }
        }   
        stage('TEST'){
            agent {
                label 'master'
            }
            steps{
                echo "testing"
                echo "${NODE_NAME}"
            }
        }
            stage('DEPLOY'){
                agent {
                label 'master'
            }
            steps{
                echo "deploying"
                echo "${NODE_NAME}"
            }
        }
    }
}
