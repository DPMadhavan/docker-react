pipeline {
  environment {
    registry = "myreactapp"
  //  registryCredential = 'awscred'
    dockerImage = ''        
 //   ECRURL = 'https://895767246702.dkr.ecr.ap-south-1.amazonaws.com/localzi-dev'
  //  ECRCRED = 'ecr:ap-south-1:awscred'
  }
  agent any
  stages {
    stage('Get SCM') {
      steps {
        sh 'rm -rf reactapp-docker'
        sh 'git clone https://github.com/DPMadhavan/docker-react.git'
        //git branch: '$BRANCH_NAME', credentialsId:'sshkey-May2021', url:'git@github.com:localzi/localzi-covid-saviour-website.git'
      }
    }
    stage('Building image') {
      steps{
        script {
	 // dockerImage = docker.build(registry + ":front_end-$BUILD_NUMBER", "--build-arg BRANCH_NAME=$BRANCH_NAME .") 
		//loc=$(pwd)
		//echo $loc
		//sh "pwd"
		   dockerImage = docker.build(registry + ":front_end-$BUILD_NUMBER")
		//sh 'docker build -f /React App with docker practise/sample/Dockerfile /React App with docker practise/sample'
        }
      }
    }
  /*  stage('Deploy Image') {
      steps{
        script {
            docker.withRegistry(ECRURL,ECRCRED) {
            dockerImage.push()          
          }
        }
      }
    }  
    stage('Pull Image') {
      steps{ 
            sshagent(credentials : ['ssh-connection-covidsaviour'], ignoreMissing: true) {	    
	      sh  '''ssh -o StrictHostKeyChecking=no ec2-user@65.1.203.226 /home/ec2-user/invoke1.sh $BUILD_NUMBER $BRANCH_NAME'''
        }
      }
    } */  
  }
}
