pipeline {
    agent any
    environment {
        MAVEN_HOME = "${MAVEN_HOME}" // Automatically populated by Jenkins
        PATH = "${MAVEN_HOME}/bin:${env.PATH}" // Add Maven binaries to PATH
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -v' // Verify Maven version
                sh 'mvn -B -DskipTests clean package' // Run Maven build
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
