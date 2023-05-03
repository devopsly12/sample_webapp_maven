pipeline {

agent any
     

stages {
    stage('Build the code') {

    steps {

     sh 'mvn clean install --file pom.xml'
    }

    
    post {
        success {

            echo 'Now Archiving....'
            archiveArtifacts artifacts: '**/target/*.jar'
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
