pipeline {
  agent any
  stages {
    stage('Code Collection') {
      steps {
        git(url: 'https://github.com/dineshmaan/simpleMavenJunit.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Compile ') {
      steps {
        sh '''mvn clean
mvn compile'''
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('Report Publish') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

  }
}