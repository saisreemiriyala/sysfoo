pipeline {
  agent any
  tools {
    maven 'Maven 3.6.3'
  }
  stages{
      stage("Build"){
          steps{
              echo 'Building ...'
              sh 'mvn compile'
              sleep 3
          }
      }
      stage("Test"){
          steps{
              echo 'Testing ...'
              sh 'mvn clean test'
              sleep 9
          }
      }
      stage("Package"){
          steps{
              echo 'Packaging ...'
              sh 'mvn package -DskipTests'
              sleep 5
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
