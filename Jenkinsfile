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
		stage('Checkout'){
			steps {
				
				sh 'mvn --version'
				sh 'docker version'
				echo "PATH $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Complile'){
			steps {
				//echo "Test"
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				echo "maven test"
				sh "mvn test"
			}
		}
		stage('Int Test'){
			steps {
				echo "Int Test"
				sh "mvn failsafe:integration-test failsafe:verify"
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