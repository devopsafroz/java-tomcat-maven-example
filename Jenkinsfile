pipeline {
    agent any
    stages {
        stage ('Build servelet Packer') {
            steps {
                /* For windows machine */
                bat 'mvn clean package'

                /* For Linux and Mac machine*/
                //sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving....'
                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }
        stage ('Deploy Build in staging area') {
            steps {
                Build job : 'Deploy_StagingArea_Pipeline'
            }
        }
    }
}