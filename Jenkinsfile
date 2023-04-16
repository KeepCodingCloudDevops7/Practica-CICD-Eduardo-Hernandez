pipeline {
  agent any
  stages {
    stage('Clean') {
      parallel {
        stage('Clean Test') {
          agent {
            node {
              label 'Ag1'
            }

          }
          steps {
            echo 'Cleaning Targets'
            sh 'mvn clean'
          }
        }

        stage('Clean Production') {
          agent {
            node {
              label 'Ag2'
            }

          }
          steps {
            echo 'Cleaning Targets'
            sh 'mvn clean'
          }
        }

      }
    }

  }
}