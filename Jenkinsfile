pipeline {
  agent any
  stages {
    stage('SCM Checkout') {
      steps {
        git(url: 'https://github.com/Wilson-D-Bui/Flexion.git', branch: 'master', changelog: true, poll: true, credentialsId: 'Wilson-D-Bui')
      }
    }
    stage('Build') {
      steps {
        sh '''#Compiles python resources for efficiency and speed

python3.6 -m py_compile'''
      }
    }
    stage('Deploy') {
      steps {
        sh '''#Deploys the python code to the TEST server

scp -i ~/.ssh/test_key $WORKSPACE/*.py ec2-user@ec2-18-217-110-31.us-east-2.compute.amazonaws.com:~/'''
      }
    }
  }
}