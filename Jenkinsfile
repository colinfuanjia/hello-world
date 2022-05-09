//Declarative script

pipeline{
	agent any
	tools {
      maven "maven3.8.4"
	}
	stages{
	   stage('GitClone'){
	     steps{
	     sh"echo cloning the latest application version"
	    git "https://github.com/colinfuanjia/hello-world"
	     }
	   }
	   stage('TestBuild'){
	     steps{
	      sh"echo running UnitTesting"
	      sh "mvn package"
	     }
	   }
	   stage("Upload"){
             steps{
                withAWS(region:"${region}", credentials:"${aws_credential})
			s3Upload(file:"${TAG_NAME}", bucket:"${bucket}", path:"${TAG_NAME}/")
	    }
	}
      } 
   

