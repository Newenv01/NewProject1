#!/usr/bin/env groovy
def workspace

pipeline{
  agent any 
  stages{
    stage('Code Check'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'JenCred', url: 'https://github.com/Newenv01/NewProject1.git']]])
        workspace = pwd()
    }
    stage('Code Compile'){
        build job: 'Code Compile', parameters: [string(name: 'workspace', value: workspace)]   
    }
    stage('Code UnitTest'){
        build job: 'Code UnitTest', parameters: [string(name: 'workspace', value: workspace)]
    }
    stage('Code Deploy'){
        build job: 'Code Deploy', parameters: [string(name: 'workspace', value: workspace)]
    }
    stage('Code Post'){
        build job: 'Code Post'
    }
  }
}
