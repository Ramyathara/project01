pipeline
{
    agent any
    //agent{label|'jenkins'}
      stages{
        stage('checkout')
        {
            steps{
                echo"scm checkout"
                git 'https://github.com/Ramyathara/project01.git'
            }
            
        }
            stage('Build')
            {steps{
            echo"build"
            sh 'mvn package'
            }
                
            }
            stage('artifact upload')
            {steps
            {
            echo"nexus"
            nexusArtifactUploader artifacts: [[artifactId: 'project01', classifier: '', file: '/home/linuxadmin/.jenkins/workspace/pipeline/target/project01.war', type: 'war']], credentialsId: 'e085c16f-135e-49cb-bee4-d919d164f522', groupId: 'asgr', nexusUrl: '10.0.0.33:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '1.0-SNAPSHOT' 
            }
            }
            stage('deploy')
            {steps
            {
                echo"deploy to webserver"
                sh 'cp /home/linuxadmin/.jenkins/workspace/project01/target/project01.war /home/linuxadmin/tomcat/apache-tomcat-9.0.94/webapps'
            }
            }
      }
}

      
        









