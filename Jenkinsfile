pipeline {
  agent any

  tools {
        maven 'maven-3.9.12'
    }
  
  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }  
      stage('unit test') {
            steps {
               sh "mvn test"
         }
      }
    }
  post {
        always {
            jacoco execPattern: '**/target/jacoco.exec',
                   classPattern: '**/target/classes',
                   sourcePattern: '**/src/main/java',
                   exclusionPattern: ''
        }
    }
}
