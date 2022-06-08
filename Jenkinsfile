pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'hello phase de test'
            sh 'mvn clean test'
          }
        }

        stage('build') {
          steps {
            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
            sh 'mvn clean install'
            archiveArtifacts 'target/*.war'
          }
        }

      }
    }

    stage('reports') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo "fin des taches, tout s\'est bien passé"'
      }
    }

  }
}