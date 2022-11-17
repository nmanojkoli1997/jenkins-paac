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
            '''
         }
        }   
        stage('TEST'){
            steps{
                echo "testing"
            }
        }
            stage('DEPLOY'){
            steps{
                echo "deploying"
            }
        }
    }
}
