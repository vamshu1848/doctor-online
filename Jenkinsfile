@Library("fortomcat") _

pipeline {
    agent any

    stages {
        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage("Tomcat Dev Deploy"){
            steps{
                tomcatdeploy("172.31.15.196", "ec2-user", "tomcat-deploy", "doctor-online.war" )
            }
        }
    }
    post {
      success {
        cleanWs()
      }
    }
}
