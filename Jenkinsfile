
/* This is a Declarative Jenkins Pipeline file.
  It defines the entire CI/CD process.
*/

pipeline {
    // 1. Agent: Specify where to run the pipeline. 'any' means any available agent.
    agent any

    // 2. Stages: Define the distinct parts of the pipeline.
    stages {
        
        // Stage 1: Checkout Code
        stage('Checkout') {
            steps {
                // This step checks out the code from your GitHub repository.
                // Jenkins will automatically get the URL from the job configuration.
                echo 'Checking out code...'
                checkout scm
            }
        }

        // Stage 2: "Build / Deploy"
        stage('Build & Deploy') {
            steps {
                // For a static HTML/CSS site, there's no "build" step (like compiling).
                // Our "deploy" step will be to archive the website files.
                // In a real-world scenario, this step might use 'ssh' or 'scp'
                // to copy files to a live web server (e.g., /var/www/html).
                echo 'Building and deploying...'
                
                // This step packages the website files and saves them with the build.
                // You can download them from the Jenkins build page.
                archiveArtifacts artifacts: '*.html', followSymlinks: false
            }
        }
    }

    // 3. Post-build Actions: Run steps after the pipeline finishes.
    post {
        success {
            // This will run only if the pipeline is successful.
            echo 'Pipeline finished successfully. Portfolio "deployed"!'
        }
        failure {
            // This will run only if the pipeline fails.
            echo 'Pipeline failed. Please review the logs.'
        }
    }
}