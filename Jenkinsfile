pipeline{
  agent any
  tools{
    maven 'Maven'
    jdk 'JDK'
  }
  stages{
    stage('Checkout'){
      steps{
        git branch:'main',url:'https://github.com/thrishaaaa/ans.git'
      }
    }
    stage('Build'){
      steps{
        sh 'mvn clean install'
      }
    }
    
    stage('Archive'){
      steps{
        archiveArtfacts artifacts : 'target/*.war' , fingerprint:true
      }
    }
    stage('Deploy'){
      steps{
        sh 'mvn clean package'
        sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
      }
    }
  }
  
}
