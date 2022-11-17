pipeline{
    agent any
    tools {
  maven 'MAVEN3.8'
}
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
            stage('MAVEN BUILD'){
                agent {
                label 'maven'
            }
            steps{
                echo "maven build"
                git 'https://github.com/Coveros/helloworld'                
                sh 'mvn clean install'
                echo "${NODE_NAME}"
                echo "${JOB_URL}console"
            }
                post {
                    success{
                        echo "archiving"
                        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
                        }
                }
        }
    }
    
}
