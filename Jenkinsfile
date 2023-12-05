pipeline{
agent any
tools{
git 'git'
}
stages{
  stage('checkout'){
    steps{
      git 'https://github.com/akshaykamthe651/Angular_CodeCoverageDemo.git'
      echo 'inside checkout'
    }
}
  stage('Sonarqube') {
    steps {
    withSonarQubeEnv('sonarqube') {
      sh "/home/ec2-user/sonar-scanner-4.6.2.2472-linux/bin/sonar-scanner"
      echo 'inside sonar scanner'
      } timeout(time: 10, unit: 'MINUTES') {
    waitForQualityGate abortPipeline: true
      echo 'inside sonar environment'
    }
  }
}

}
}
