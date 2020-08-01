pipeline{
    agent any
    tools{
        maven 'local maven'
    }
    stages{
        stage('SCM'){
            steps{
                    git branch: 'master', url: 'https://github.com/sreenugvk/SampleSpringWebMvc.git'
            }
        
        }
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