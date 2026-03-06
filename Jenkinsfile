pipeline {
    agent any 
    
    stages {
        stage("Cleanup workspace") {
            steps {
                cleanWs()
            }
        }
        
        stage("Go to github and clone the repo") {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/ekelejames/bash-script'
            }
        }
        
        stage("Run the bash script that is in the repo") {
            steps {
                script {
                    sh "chmod +x script.sh"
                    sh "./script.sh"
                }
            }
        }

    }
    
    post {
        success {
            echo "Successfully ran the script"
        }
        failure {
            echo "The pipeline failed!"
        }
    }
}