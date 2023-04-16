pipeline {
  agent {
    node {
      label 'Ag1'
    }

  }
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

    stage('Build') {
      parallel {
        stage('Build Test') {
          steps {
            echo 'Building Artifacts'
            sh '''mvn compile
'''
            archiveArtifacts 'Hello'
          }
        }

        stage('Build Production') {
          agent {
            node {
              label 'Ag2'
            }

          }
          steps {
            echo 'Building Artifacts'
            sh 'mvn compile'
          }
        }

      }
    }

  }
}