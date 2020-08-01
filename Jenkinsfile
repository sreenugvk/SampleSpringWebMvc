pipeline{
    agent any
    tools{
        maven 'local maven'
    }
    stages{
        stage('Compile Stage'){
            steps{
                    sh 'mvn clean compile'
            }
        }
        stage ('Testing Stage'){
            steps{
                    sh 'mvn test'
            }
        }
        stage('Package'){
            steps{
                    sh 'mvn package'
            }
            post {
                success {
                    echo 'Now archiving the Artifacts'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
    }
}