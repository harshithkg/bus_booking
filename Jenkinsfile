@Library('my-shared-library@main') _  // Correct syntax

pipeline {
    agent { label 'slave-2' }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        MAVEN_HOME = '/usr/share/maven'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                pipeline.checkout()
            }
        }

        stage('Set up Java 17') {
            steps {
                pipeline.setupjava()
            }
        }

        stage('Set up Maven') {
            steps {
                pipeline.mavensetup()
            }
        }

        stage('Build with Maven') {
            steps {
                pipeline.build()
            }
        }

        stage('Upload Artifact') {
            steps {
                uploadArtifact('target/bus-booking-app-1.0-SNAPSHOT.jar')
            }
        }

        stage('Run Application') {
            steps {
                pipeline.runApp()
            }
        }

        stage('Validate App is Running') {
            steps {
                pipeline.validateApp()
            }
        }
        stage('wait') {
        steps {
            pipeline.wait()
        }
        }
        stage('stoping') {
        steps {
            pipeline.stop()
        }
        }
         stage('cleaning') {
        steps {
            pipeline.clean()
        }
        }        
stage('sending a mail') {
        steps {
            pipeline.mail()
        }
        }
    }
}
