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
        stage('Deploy To Staging Environment'){
            steps{
                build job: 'deploy_application_staging_env'
            }
        }
        stage('Deploye to Prod'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message: 'Approve Production Depooyment'
                }
                build job: 'deploy_App_Prod'
            }
        }
    }
}