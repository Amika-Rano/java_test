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
            sh 'ls'
            git(url: 'https://github.com/Amika-Rano/java_test.git', branch: 'main')
            sh 'mvn clean install'
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