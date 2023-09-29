pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Compile Maven App'
        sh 'mvn compile'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Test Maven App'
            sh 'mvn clean test'
          }
        }

        stage('SCA') {
          steps {
            sleep 5
          }
        }

      }
    }

    stage('Package') {
      steps {
        echo 'Package Maven App'
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
}