pipeline {
  agent any
  stages {
    stage('SCM for java code ') {
      steps {
        git(url: 'https://github.com/kholoodi11/simpleMavenJunit.git', branch: 'master', poll: true)
      }
    }

    stage('Maven Compile ') {
      steps {
        sh '''mvn clean
mvn compile '''
      }
    }

    stage('Test ') {
      steps {
        sh 'mvn test'
        sh 'echo "Testing is done..!"'
      }
    }

    stage('Package ') {
      steps {
        sh 'mvn package'
      }
    }

    stage('Publish Test Result') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('Deployment ') {
      steps {
        sh 'java -jar target/*.jar'
      }
    }

  }
}