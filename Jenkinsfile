pipeline {
  agent any
  tools { 
        maven 'Maven_3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=qabuggywebapp -Dsonar.organization=qabuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=c04c2993c61c01642cdcbd6cf105874f625cb6e8'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'e66b0888-da28-48de-85ab-ebe2d8f19578', variable: 'e66b0888-da28-48de-85ab-ebe2d8f19578')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
