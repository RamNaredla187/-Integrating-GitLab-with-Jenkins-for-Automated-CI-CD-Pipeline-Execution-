pipeline {
    agent any

    environment {
        // Set Java home environment variable (adjust based on your system setup)
        JAVA_HOME = '/usr/lib/jvm/java-11-openjdk-amd64' // Example path for Java 11
    }

    triggers {
        // Poll the SCM (source code management system) for changes every minute
        pollSCM('* * * * *') // This cron expression means "every minute"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from GitLab
                git branch: 'main', 
                    credentialsId: '######', 
                    url: 'https://gitlab.com/your-username/your-repository.git'
            }
        }

        stage('Compile') {
            steps {
                script {
                    // Compile the Java code using javac
                    sh 'javac sample.java'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // Run the compiled Java program using java
                    sh 'java sample'
                }
            }
        }

        stage('Post-Build') {
            steps {
                // Optional: Perform cleanup or notifications
                echo 'Build and execution complete!'
            }
        }
    }

    post {
        always {
            // Clean up or perform actions regardless of success or failure
            echo 'Pipeline execution finished.'
        }
    }
}
