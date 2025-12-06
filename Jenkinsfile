pipeline {
    agent any

    stages {
        stage('Create Directory For web application') {
            steps {
                //First, Drop the directory if exist
                sh 'rm -rf /var/lib/jenkins/tomcat-shop'
                // Create the Directory
                sh 'mkdir /var/lib/jenkins/tomcat-shop'

            }
        }
        stage('Drop the apache docker container'){
            steps{
                echo 'Dropping the container...'
                sh 'docker rm -f tomcat1'
            }
        }
        stage('Create the Tomcat container'){
            steps{
                echo 'Creating the container'
                sh 'docker run -dit --name tomcat1 -p 9090:8080  -v /var/lib/jenkins/tomcat-shop:/usr/local/tomcat/webapps tomcat:9.0'
            }
        }
        stage('Copy the web application to the container directory'){
            steps{
                echo 'Copying the shopping appplication'
                sh 'cp -r shopping/* /var/lib/jenkins/tomcat-shop'
            }
        }

    }
}
