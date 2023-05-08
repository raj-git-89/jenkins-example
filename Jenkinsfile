pipeline {
    agent any
    stages {
        stage("Clean Up") {
            steps{
                deleteDir()
            }
        }
        stage("Clone Repo") {
            steps{
                sh "git clone https://github.com/raj-git-89/jenkins-example.git"
            }
        }
        stage("Build") {
            steps{
                dir("jenkins-example"){
                    sh "mvn clean install"
                }
            }
        }
        stage("Test") {
            steps{
                dir("jenkins-example") {
                    sh "mvn test"
                }
            }
        }
        stage("Code Scan") {
            steps {
                echo "SonarQube code scan for code coverage."
            }
        }
        stage("Docker Build"){
            steps {
                echo "In this stage Docker Image will be created."
            }
        }
        stage("Upload to staging repo") {
            steps{
                echo "In this stage Docker Image will be pushed to a staging rpository(Nexus)."
            }
        }
        stage("Upload Helm Chart to staging repo"){
            steps {
                echo "In this stage Helm chart will be pushed to a staging rpository(Nexus)."
            }
        }
        stage("Deploy Microservice to Test Namespace"){
            steps {
                echo "In this stage test namespace will be created and the microservice along with the backend service and wiremock will be deployed using helm."
            }
        }
        stage("Testing of Microservice post deployment"){
            steps {
                echo "In this stage Helm chart will be pushed to a staging rpository(Nexus)."
            }
        }
        stage("Upload artifacts to release repo"){
            steps {
                echo "In this stage the helm chart and docker image will be uploaded to the release repo,form which the CD will be able to pick the artifacts.This stage will only run for release branches."
            }
        }
        stage("Post Clean up stage"){
            steps {
                echo "In this stage the namespace will be deleted and the workspace will be cleaned "
                deleteDir()
            }
        }
    }
}