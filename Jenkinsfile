pipeline {

agent any
     

stages {
    stage('Build the code') {

    steps {

     sh 'mvn clean install --file demo/pom.xml'
    }

    
    post {
        success {

            echo 'Now Archiving....'
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }

    }
    stage('UNIT TEST'){
            steps {
                sh 'mvn test'
            }
        }

	stage('INTEGRATION TEST'){
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
            post {
                success { 

                    echo 'test'
                }
            }
        }


}
}
