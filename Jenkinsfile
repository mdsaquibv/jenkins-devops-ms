// Scripted Pipelines
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('int test'){
// 		echo "int test"
// 	}
// }

// Declarative Pipelines
pipeline{
	//agent { docker { image 'maven:3.6.3'}}
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Build'){
			steps {
				
				sh 'maven --version'
				sh 'docker version'
				echo "PATH $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Test'){
			steps {
				echo "Test"
			}
		}
		stage('Int Test'){
			steps {
				echo "Int Test"
			}
		}
	}

	post {
		always {
			echo 'I am awesome, I run always'
		}
		success{
			echo 'I run when you are success'
		}
		failure{
			echo 'I run when you fail'
		}
	}
}