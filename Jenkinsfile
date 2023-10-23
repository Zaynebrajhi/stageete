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
        sh "git clone https://github.com/Zaynebrajhi/stageete.git"
      }
    }
    stage ("Generate backend image"){
      steps{
        dir("stageete/employeeback"){
          sh "mvn clean install -DskipTests=true"
          sh "docker build -t devopsangular ."
        }
      }
    }
    stage ("Build Angular"){
  steps {
    dir("stageete/empfrond"){ 
       
        sh "docker build -t angular ."  
    }
  }
}
    stage ("Run docker compose"){
      steps { 
        dir("devopsangularr"){
        sh "docker compose up -d"
      }}}}}
