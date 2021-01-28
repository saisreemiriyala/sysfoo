pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'Building ...'
        sh 'mvn compile'
        sleep 3
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'Testing ...'
        sh 'mvn clean test'
        sleep 9
      }
    }

    stage('Package') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'Packaging ...'
        sh 'mvn package -DskipTests'
        sleep 5
      }
    }

    stage('') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("sais4/sysfoo:v${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
            dockerImage.push("dev")
          }
        }

      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}