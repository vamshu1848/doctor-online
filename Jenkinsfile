@Library("fortomcat") _

pipeline {
    agent any

    stages {
        stage('Code Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vamshu1848/doctor-online'
            }
        }
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
