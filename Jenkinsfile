node{
 stage('Source'){
    checkout scm
 }
  def mvnHome = tool 'Apache_maven'
 stage('Build'){
      sh "${mvnHome}/bin/mvn clean install" 
  }
  stage('CodeQualityCheck'){
      sh "${mvnHome}/bin/mvn clean sonar:sonar" 
  }
  stage('UploadArtifacts'){
      sh "${mvnHome}/bin/mvn clean deploy" 
  }
  /*stage('DeployApplication'){
     sshagent(['chefid']) {
      sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 172.16.151.77 uname -a'
     }
  }
 stage('Run Selenium Test'){
    dir ("D:\\PROJECT_INFO\\DEVOPS\\selenium_project_bat_file") { 
        sh 'Selenium.bat' 
     } 
  }*/
  stage('Performane Tests'){
                sh '''/:
				cd /opt/apache-jmeter-3.1/bin
	            jmeter -n -t /opt/apache-jmeter-3.1/extras/Test.jmx -l /opt/apache-jmeter-3.1/demo-report.jtl'''
              
    			performanceReport compareBuildPrevious: false, configType: 'ART', errorFailedThreshold: 0, errorUnstableResponseTimeThreshold: '', errorUnstableThreshold: 0, failBuildIfNoResultFile: false, modeOfThreshold: false, modePerformancePerTestCase: true, modeThroughput: false, nthBuildNumber: 0, parsers: [[$class: 'JMeterParser', glob: '/opt/apache-jmeter-3.1/demo-report.jtl']], relativeFailedThresholdNegative: 0, relativeFailedThresholdPositive: 0, relativeUnstableThresholdNegative: 0, relativeUnstableThresholdPositive: 0
            }
   }
 
