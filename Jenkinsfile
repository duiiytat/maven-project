pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh '/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/localMaven/bin/mvn clean package'
            }
            post {
                success {
                    echo 'Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'Deploy-to-staging'
            }
        }
    }
}
