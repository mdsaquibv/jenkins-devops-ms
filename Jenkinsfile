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
	agent { docker { image 'maven:3.6.3'}}
	stages {
		stage('Build'){
			steps {
				
				sh 'maven --version'
				echo "Build"
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