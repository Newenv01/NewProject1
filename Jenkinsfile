#!/usr/bin/env groovy
def workspace

pipeline{
  agent any 
  stages{
    stage('Code Check'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'JenCred', url: 'https://github.com/Newenv01/NewProject1.git']]])
        workspace = pwd()
        sh "mvn clean package"
      }
    }
    stage('Code Compile'){
      steps{
        build job: 'Code Compile', parameters: [string(name: 'workspace', value: workspace)]   
      }
    }
    stage('Code UnitTest'){
      steps{
        build job: 'Code UnitTest', parameters: [string(name: 'workspace', value: workspace)]
      }
    }
    stage('Code Deploy'){
      steps{
        build job: 'Code Deploy', parameters: [string(name: 'workspace', value: workspace)]
      }
    }
    stage('Code Post'){
      steps{
        build job: 'Code Post'
      }
    }
  }
}
