pipeline {
    agent any
    tools { 
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn install'
            }
        }
        
        stage ('Scantist') {
            steps {
                sh '''
                    export SCANTIST_IMPORT_URL=https://api.scantist.io/ci-scan/
                    export SCANTISTTOKEN=8dc0ef6d-8c4e-4b22-b6fe-298c4722b440

                    curl -s https://scripts.scantist.com/staging/scantist-bom-detect.jar --output scantist-bom-detect.jar

                    java -jar scantist-bom-detect.jar
                '''
            }
        }
    }
}
