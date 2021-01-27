pipeline {
  agent any
  tools {
    maven 'Maven 3.6.3'
  }
  stages{
      stage("Build"){
          steps{
              echo 'Building ...'
              sleep 3
          }
      }
      stage("Test"){
          steps{
              echo 'Testing ...'
              sleep 9
          }
      }
      stage("Package"){
          steps{
              echo 'Packaging ...'
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
