#!/usr/bin/env groovy
def workspace

pipeline{
  agent any 
  stages{
    stage('Code Check'){
      steps{
        dir
        mkdir TestDir
      }
    }
    stage('Code Compile'){
      steps{
        dir TestDir
      }
    }
    stage('Code UnitTest'){
      steps{
        cd TestDir
      }
    }
    stage('Code Deploy'){
      steps{
        echo "TestDir Created"
      }
    }
    stage('Code Post'){
      steps{
        echo "This is End"
      }
    }
  }
}
