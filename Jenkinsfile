pipeline {
    agent none

    environment {
        // Set the JDK to use (configure this in Jenkins Global Tool Configuration)
        JAVA_HOME = '/opt/java/openjdk'
    }

    stages {
        stage('Build and Package on MyNode') {
            agent {
                label 'jdk17'  // Specify the label of your Jenkins node
            }
            steps {
                script {
                    // Clean and build the Maven project
                    sh 'mvn clean package'
                }
            }
        }

        stage('Publish Artifacts on MyNode') {
            agent {
                label 'jdk17'  // Specify the label of your Jenkins node
            }
            steps {
                script {
                    // Archive the built artifacts (e.g., JAR file)
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }

        // Add more stages as needed (testing, deployment, etc.)
    }
}
