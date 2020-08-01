pipeline{
    agent any
    stages{
        stage('Compile Stage'){
            steps{
                withMaven(maven : 'local maven'){
                    sh 'mvn clean compile'
                }
            }
        }
        stage ('Testing Stage'){
            steps{
                withMaven(maven: 'local maven'){
                    sh 'mvn test'
                }
            }
        }
        stage('Package'){
            steps{
                withMaven(maven: 'local maven'){
                    sh 'mvn package'
                }
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