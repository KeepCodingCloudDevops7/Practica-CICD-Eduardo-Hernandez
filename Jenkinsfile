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
          agent {
            node {
              label 'Ag1'
            }

          }
          steps {
            echo 'Building Artifacts'
            sh '''mvn compile
'''
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

    stage('Test') {
      parallel {
        stage('Test') {
          agent {
            node {
              label 'Ag1'
            }

          }
          steps {
            echo 'Running Tests'
            sh 'mvn test'
          }
        }

        stage('Test Production') {
          agent {
            node {
              label 'Ag2'
            }

          }
          steps {
            echo 'Running Tests'
            sh 'mvn test'
          }
        }

      }
    }

  }
}