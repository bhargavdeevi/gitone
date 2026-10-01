@Library('devops-shared-library') _
pipeline {
    agent any
    tools {
        maven 'mymaven'
    }
    stages {
        stage ("CheckoutCode") {
            steps {
                checkoutCode()
            }
        }
        stage ("MavenBuild") {
            steps {
                mavenBuild()
            }
        }
        stage ("DockerBuild") {
            steps {
                dockerBuild('bhargavdeevi/jenkins-shared', "${BUILD_NUMBER}")
            }
        }
        stage ("DockerPush") {
            steps {
                script {
                    dockerPush('bhargavdeevi/jenkins-shared', "${BUILD_NUMBER}")
                }
            }
        }
    }
}
