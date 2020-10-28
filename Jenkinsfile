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
                    curl -s https://scripts.scantist.com/staging/scantist-bom-detect.jar --output scantist-bom-detect.jar

                    java -jar scantist-bom-detect.jar
                '''
            }
        }
    }
}

