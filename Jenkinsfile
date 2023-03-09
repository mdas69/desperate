pipeline
{
  agent any
  tools {
  	maven 'Maven_Mdas' 
 	}
 	
 	stages
 	{
 
  		stage('Test'){
 			steps{
 				catchError(buildResult: 'SUCCESS' , stageResult: 'FAILURE'){
 				git 'https://github.com/mdas69/desperate.git'
 				bat "mvn clean install"
 				}
 			}
 		}
 	
 	
 	
 		stage ('Publish Allure Reports'){
 			steps {
 				script {
 		 		allure ([
 		 			includeProperties: false,
 		 			jdk: '',
 		 			properties: [],
					reportBuildPolicy: 'ALWAYS',
					results: [[path: '/allure-results']]
						])
					}
				}
			}


		stage ('Publish Extent Report'){
			steps{
				publishHTML([allowMissing: false,
				alwaysLinkToLastBuild: false,
				keepAll: false,
				reportDir: 'build_Extent_Report_mdas',
				reportFiles: 'mdas_TestExecutionReport.html',
				reportName: 'HTML Extent Report',
				reportTitles: ''])
				}
			}
			
	}		
}		
			
