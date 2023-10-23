pipeline{
  agent any 
  tools {
    maven 'maven'
    nodejs 'node'
  }
  stages {
    stage ("Clean up"){
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo"){
      steps {
        sh "git clone https://github.com/Zaynebrajhi/devopsangularr.git"
      }
    }
    stage ("Generate backend image"){
      steps{
        dir("devopsangularr/springboot/app"){
          sh "mvn clean install"
          sh "docker build -t devopsangular ."
        }
      }
    }
    stage ("Build Angular"){
  steps {
    dir("devopsangularr/angular-app"){ 
       
        sh "docker build -t angular ."  
    }
  }
}
    stage ("Run docker compose"){
      steps { 
        dir("devopsangularr"){
        sh "docker compose up -d"
      }}}}}
