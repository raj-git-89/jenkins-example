pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/raj-git-89/jenkins-example.git'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'local_maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'local_maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'local_maven') {
                    sh 'mvn install'
                }
            }
        }

         stage ('deploy to tomcat') {
             steps {
                 sshagent(['tomcat']) {
                    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.35.4:/var/lib/tomcat/webapps'
                    }
             }
   }
}
}
